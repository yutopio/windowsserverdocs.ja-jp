---
title: Azure 拡張ネットワークを使用してオンプレミスのサブネットを Azure に拡張する
description: Azure 拡張ネットワークを使用してオンプレミスのサブネットを Azure に拡張する
ms.technology: manage
ms.topic: article
author: grcusanz
ms.author: grcusanz
ms.date: 12/17/2019
ms.localizationpriority: medium
ms.prod: windows-server
ms.openlocfilehash: 29e370da31b02a475f0fdd5d7914348189ca616b
ms.sourcegitcommit: 6a245fefdf958bfc0aeb69f7a887d11a07bdcd23
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2020
ms.locfileid: "94570357"
---
# <a name="extend-your-on-premises-subnets-into-azure-using-azure-extended-network"></a>Azure 拡張ネットワークを使用してオンプレミスのサブネットを Azure に拡張する

> 適用先:Windows Admin Center、Windows Admin Center Preview

## <a name="overview"></a>概要

Azure 拡張ネットワークを使用すると、オンプレミスのサブネットを Azure に拡張して、オンプレミスの仮想マシンが Azure に移行するときに元のオンプレミスのプライベート IP アドレスを保持できるようにすることができます。

ネットワークは、仮想アプライアンスとして機能する2つの Windows Server 2019 Vm 間の双方向の VXLAN トンネルを使用して拡張されます。1つはオンプレミスで実行され、もう1つは Azure で実行されており、それぞれが拡張されるサブネットにも接続されています。
拡張する各サブネットには、1組のアプライアンスが必要です。 複数のサブネットは、複数のペアを使用して拡張できます。

> [!NOTE]
> Azure 拡張ネットワークは、Azure に移行するときに IP アドレスを変更できないマシンにのみ使用してください。 必要に応じて、IP アドレスを変更し、Azure に完全に存在するサブネットに接続することをお勧めします。

## <a name="planning"></a>計画

Azure 拡張ネットワークを使用する準備を行うには、ストレッチするサブネットを特定し、次の手順を実行する必要があります。

### <a name="capacity-planning"></a>容量計画

Azure 拡張ネットワークを使用して最大250の IP アドレスを拡張できます。 Azure 拡張ネットワーク仮想アプライアンスの CPU 速度によっては、約 700 Mbps の合計スループットを予想できます。

### <a name="configuration-in-azure"></a>Azure での構成

Windows 管理センターを使用する前に、Azure Portal で次の手順を実行する必要があります。

1. ゲートウェイ接続に必要なサブネットに加えて、少なくとも2つのサブネットを含む仮想ネットワークを Azure に作成します。 作成するサブネットの1つは、拡張するオンプレミスのサブネットと同じサブネット CIDR を使用する必要があります。 サブネットは、オンプレミスのサブネットと重複しないように、ルーティングドメイン内で一意である必要があります。

2. 仮想ネットワークをオンプレミスネットワークに接続するために、サイト間接続または ExpressRoute 接続を使用するように仮想ネットワークゲートウェイを構成します。

3. 入れ子になった仮想化を実行できる Windows Server 2019 VM を Azure に作成します。 これは2つの仮想アプライアンスの1つです。 プライマリネットワークインターフェイスをルーティング可能なサブネットに接続し、2つ目のネットワークインターフェイスを拡張サブネットに接続します。

4. VM を起動し、Hyper-v の役割を有効にして、再起動します。 次に例を示します。

    ```powershell
    Install-WindowsFeature -Name Hyper-V -IncludeManagementTools -Restart
    ```

5. VM に2つの外部仮想スイッチを作成し、各ネットワークインターフェイスに接続します。 次に例を示します。

    ```powershell
    New-VMSwitch -Name "External" -AllowManagementOS $true -NetAdapterName "Ethernet"
    New-VMSwitch -Name "Extended" -AllowManagementOS $true -NetAdapterName "Ethernet 2"
    ```

### <a name="on-premises-configuration"></a>オンプレミスの構成

オンプレミスの仮想アプライアンスとして機能する VM の作成など、オンプレミスのインフラストラクチャでいくつかの手動構成を実行する必要もあります。

1. オンプレミスの VM (仮想アプライアンス) をデプロイする物理マシンでサブネットが使用可能であることを確認します。 これには、拡張するサブネットと、Azure 仮想ネットワーク内のサブネットと重複しない、一意の2番目のサブネットが含まれます。

2. 入れ子になった仮想化をサポートするハイパーバイザー上に Windows Server 2019 VM を作成します。 これはオンプレミスの仮想アプライアンスです。 これは、クラスター内の高可用性 VM として作成することをお勧めします。 仮想ネットワークアダプターをルーティング可能なサブネットに接続し、2つ目の仮想ネットワークアダプターを拡張サブネットに接続します。

3. VM を起動し、VM の PowerShell セッションから次のコマンドを実行して Hyper-v ロールを有効にし、VM を再起動します。

    ```powershell
    Install-WindowsFeature -Name Hyper-V -IncludeManagementTools -Restart
    ```

4. VM 内の PowerShell セッションで次のコマンドを実行して、VM に2つの外部仮想スイッチを作成し、各ネットワークインターフェイスに接続します。

    ```powershell
    New-VMSwitch -Name "External" -AllowManagementOS $true -NetAdapterName "Ethernet"
    New-VMSwitch -Name "Extended" -AllowManagementOS $true -NetAdapterName "Ethernet 2"
    ```

### <a name="additional-prerequisites"></a>追加の前提条件

オンプレミスネットワークと Azure の間にファイアウォールがある場合は、非対称ルーティングを許可するように構成する必要があります。 これには、シーケンス番号のランダム化を無効にし、TCP 状態のバイパスを有効にする手順が含まれる場合があります。 これらの手順については、ファイアウォールベンダーのドキュメントを参照してください。

## <a name="deploy"></a>配置

展開は Windows 管理センターを通じて行われます。

### <a name="install-and-configure-windows-admin-center"></a>Windows 管理センターのインストールと構成

1. Windows 管理センターを、前に作成した2つの仮想アプライアンス以外の Windows 管理センターを実行できる任意のコンピューターに[ダウンロードしてインストールし](../understand/windows-admin-center.md)ます。

2. Windows 管理センターで、[ **設定** ] (ページの右上隅) > [ **拡張機能** ] を選択します。 次に、[ **拡張機能** ] を選択します。

    ![[設定] の [利用可能な拡張] タブを示すスクリーンショット](../media/azure-extended-network/installed-extensions.png)

3. [ **使用可能な拡張** ] タブで、[ **Azure 拡張ネットワーク** ] を選択し、[ **インストール** ] を選択します。

    数秒後に、インストールが成功したことを示すメッセージが表示されます。

4. [Windows 管理センターを Azure に接続](azure-integration.md)します (まだインストールしていない場合)。 ここでこの手順を省略した場合は、後でこの手順を実行することをお勧めします。

5. Windows 管理センターで、[ **すべての接続**  >  ] [ **追加** ] の順に選択し、[ **windows Server** ] タイルの [ **追加** ] を選択します。 オンプレミスの仮想アプライアンスのサーバー名 (および必要に応じて資格情報) を入力します。

    ![オンプレミスの仮想アプライアンス上のサーバーマネージャーで Azure 拡張ネットワークツールを表示している Windows 管理センターのスクリーンショット](../media/azure-extended-network/azure-extended-network.png).

6. [ **Azure 拡張ネットワーク** ] をクリックして開始します。 最初に [概要] と [セットアップ] ボタンが表示されます。

    ![イメージ](../media/azure-extended-network/azure-extended-network-intro.png)

### <a name="deploy-azure-extended-network"></a>Azure 拡張ネットワークをデプロイする

1. [ **セットアップ] を** クリックして構成を開始します。

2. [ **次へ** ] をクリックして、概要を終了します。

3. [ **パッケージのアップロード** ] パネルで、Azure 拡張ネットワークエージェントパッケージをダウンロードし、仮想アプライアンスにアップロードする必要があります。 パネルの指示に従います。

    > [!IMPORTANT]
    > 必要に応じて下にスクロールし、[ **アップロード** ] をクリックしてから [次へ] をクリックします。 **Extended-Network セットアップ**

4. 拡張するオンプレミスネットワークのサブネット CIDR を選択します。 サブネットの一覧は、仮想アプライアンスから読み込まれます。 仮想アプライアンスを正しいサブネットのセットに接続していない場合、この一覧には目的のサブネット CIDR が表示されません。

5. サブネット CIDR を選択したら、[ **次へ** ] をクリックします。

6. 拡張するサブスクリプション、リソースグループ、仮想ネットワークを選択します。

    ![Azure ネットワーク](../media/azure-extended-network/azure-network.png)

    リージョン (Azure の場所) とサブネットが自動的に選択されます。 [次へ: Extended-Network ゲートウェイセットアップ] を選択して続行します。

7. 次に、仮想アプライアンスを構成します。 オンプレミスのゲートウェイの情報を自動的に入力する必要があります。

    ![オンプレミスネットワークゲートウェイ](../media/azure-extended-network/on-premises-network-gateway.png)

    正しく表示されている場合は、[ **次へ** ] をクリックします。

8. Azure 仮想アプライアンスの場合は、使用するリソースグループと VM を選択する必要があります。

    ![Azure ネットワークゲートウェイ](../media/azure-extended-network/azure-network-gateway.png)

9. VM を選択した後、Azure Extended-Network ゲートウェイサブネット CIDR も選択する必要があります。 次に、[ **次へ** ] をクリックします。

10. 概要情報を確認し、[ **展開** ] をクリックしてデプロイプロセスを開始します。 デプロイには約5-10 分かかります。 デプロイが完了すると、拡張 IP アドレスを管理するための次のパネルが表示され、状態は **[OK]** になります。

    ![インストールの完了](../media/azure-extended-network/installation-complete.png)

## <a name="manage"></a>管理する

拡張ネットワーク経由でアクセスできるようにする各 IP アドレスを構成する必要があります。 最大250のアドレスを拡張するように構成できます。
アドレスを拡張するには

1. [ **IPv4 アドレスの追加** ] をクリックします。

    ![Ipv4 アドレスの追加](../media/azure-extended-network/add-ipv4-addresses.png)

2. 右側に [ **新しい IPv4 アドレスを追加** します。

    ![Ipv4 アドレスパネルの追加](../media/azure-extended-network/add-ipv4-addresses-panel.png)

3. アドレスを手動で追加するには、[ **追加** ] ボタンを使用します。 オンプレミスに追加したアドレスは、azure アドレス一覧に追加した Azure アドレスによって到達可能になります (その逆も同様です)。

4. Azure Extended Network は、ネットワークをスキャンして IP アドレスを検出し、このスキャンに基づいて候補リストを設定します。 これらのアドレスを拡張するには、ドロップダウンリストを使用して、検出されたアドレスの横にあるチェックボックスをオンにする必要があります。 すべてのアドレスが検出されるとは限りません。 必要に応じて、[ **追加** ] ボタンを使用して、自動的に検出されないアドレスを手動で追加します。

    ![情報を含む ipv4 アドレスパネルを追加する](../media/azure-extended-network/add-ipv4-addresses-panel-filled.png)

5. 完了したら、[ **送信** ] をクリックします。 構成が完了すると、状態が [ **更新中** ]、[ **進行** 中 **]、[OK]** に変わります。

    アドレスが拡張されました。 [IPv4 アドレスの追加] ボタンを使用して、いつでも他のアドレスを追加します。 拡張ネットワークのいずれかの側で IP アドレスが使用されなくなった場合は、その横にあるチェックボックスをオンにして、[IPv4 アドレスの削除] を選択します。

Azure 拡張ネットワークを使用する必要がなくなった場合は、[ **Azure 拡張** ネットワークの削除] ボタンをクリックします。 これにより、2つの仮想アプライアンスからエージェントがアンインストールされ、拡張 IP アドレスが削除されます。 ネットワークが拡張されなくなります。 拡張ネットワークの使用を再度開始する場合は、削除後にセットアップを再実行する必要があります。

## <a name="troubleshooting"></a>トラブルシューティング

Azure 拡張ネットワークのデプロイ中にエラーが発生した場合は、次の手順を実行します。

1. 両方の仮想アプライアンスが Windows Server 2019 を使用していることを確認します。

2. いずれかの仮想アプライアンスで Windows 管理センターが実行されていないことを確認します。 Windows 管理センターは、オンプレミスネットワークから実行することをお勧めします。

3. を使用して、Windows 管理センターゲートウェイからオンプレミスの VM にリモートで配置できることを確認し `enter-pssession` ます。

4. Azure とオンプレミスの間にファイアウォールがある場合は、選択したポートで UDP トラフィックを許可するように構成されていることを確認します (既定では 4789)。 Ctstrが Ic などのツールを使用して、リスナーと送信者を構成します。 指定されたポートで双方向でトラフィックを送信できることを確認します。

5. Pktmon を使用して、パケットが予期したとおりに送受信されていることを確認します。 各仮想アプライアンスで pktmon を実行します。

    ```powershell
    Pktmon start –etw
    ```

6. Azure 拡張ネットワーク構成を実行してから、トレースを停止します。

    ```powershell
    Pktmon stop
    Netsh trace convert input=<path to pktmon etl file>
    ```

7. 各仮想アプライアンスから生成されたテキストファイルを開き、指定されたポート (既定では 4789) で UDP トラフィックを検索します。 オンプレミスの仮想アプライアンスから送信されたトラフィックが Azure 仮想アプライアンスによって受信されていない場合は、アプライアンス間のルーティングとファイアウォールを確認する必要があります。 オンプレミスから Azure に送信されたトラフィックがある場合は、Azure 仮想アプライアンスが応答でパケットを送信することを確認する必要があります。 このパケットがオンプレミスの仮想アプライアンスによって受信されない場合は、ルーティングが正しいこと、および間でトラフィックをブロックしているファイアウォールがないことを確認する必要があります。

### <a name="diagnosing-the-data-path-after-initial-configuration"></a>初期構成後のデータパスの診断

Azure 拡張ネットワークを構成すると、通常、ファイアウォールがトラフィックをブロックしているか、障害が断続的に発生した場合に MTU を超えたことが原因で発生する可能性のある追加の問題が発生します。

1. 両方の仮想アプライアンスが稼働していることを確認します。

2. Azure 拡張ネットワークエージェントが各仮想アプライアンスで実行されていることを確認します。

    ```powershell
    get-service extnwagent
    ```

3. 状態が [実行中] でない場合は、次のようにして開始できます。

    ```powershell
    start-service extnwagent
    ```

4. 上記の手順5で説明したように packetmon を使用します。拡張ネットワーク上の2つの Vm 間でトラフィックが送信され、構成されている UDP ポートを介して送信され、もう一方の仮想アプライアンスによって受信および転送されることを確認します。
