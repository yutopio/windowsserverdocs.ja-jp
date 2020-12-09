---
title: HYPER-V 仮想マシン用の仮想スイッチを作成します。
description: Hyper-v マネージャーまたは Windows PowerShell を使用して仮想スイッチを作成する手順について説明します。
ms.topic: get-started-article
ms.assetid: fdc8063c-47ce-4448-b445-d7ff9894dc17
ms.author: benarm
author: BenjaminArmstrong
ms.date: 10/04/2016
ms.openlocfilehash: 1bb5c6492896cfdaaf9446502e0eee36ef7dd46a
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96866141"
---
# <a name="create-a-virtual-switch-for-hyper-v-virtual-machines"></a>HYPER-V 仮想マシン用の仮想スイッチを作成します。

>適用対象: Windows 10、Windows Server 2016、Microsoft Hyper-V Server 2016、Windows Server 2019、Microsoft Hyper-V Server 2019

仮想スイッチを使用すると、Hyper-v ホスト上で作成された仮想マシンが他のコンピューターと通信できるようになります。 Windows Server に Hyper-v の役割を初めてインストールするときに、仮想スイッチを作成できます。 追加の仮想スイッチを作成するには、Hyper-v マネージャーまたは Windows PowerShell を使用します。 仮想スイッチの詳細については、「[Hyper-V 仮想スイッチ](../../hyper-v-virtual-switch/Hyper-V-Virtual-Switch.md)」を参照してください。

仮想マシンネットワークは複雑なサブジェクトになることがあります。 また、 [スイッチ埋め込みチーミング (SET)](../../hyper-v-virtual-switch/RDMA-and-Switch-Embedded-Teaming.md#switch-embedded-teaming-set)と同様に、いくつかの新しい仮想スイッチ機能を使用することもできます。 しかし、基本的なネットワークはとても簡単です。 このトピックでは、Hyper-v でネットワーク化された仮想マシンを作成できるように、十分に説明します。 ネットワークインフラストラクチャをセットアップする方法の詳細については、 [ネットワーク](../../../networking/index.yml) のドキュメントを参照してください。

## <a name="create-a-virtual-switch-by-using-hyper-v-manager"></a>Hyper-v マネージャーを使用して仮想スイッチを作成する

1.  Hyper-v マネージャーを開き、Hyper-v ホストコンピューター名を選択します。

2.  [**アクション**] [  >  **仮想スイッチマネージャー**] を選択します。

    ![仮想スイッチマネージャー > メニューオプションアクションを示すスクリーンショット](../media/Hyper-V-Action-VSwitchManager.png)

3.  目的の仮想スイッチの種類を選択します。

    |接続の種類|説明|
    |-------------------|---------------|
    |外部|外部ネットワーク上のサーバーおよびクライアントと通信するために、仮想マシンに物理ネットワークへのアクセスを提供します。 同じ Hyper-v サーバー上の仮想マシンが相互に通信できるようにします。|
    |内部|同じ Hyper-v サーバー上の仮想マシン間、および仮想マシンと管理ホストオペレーティングシステムの間の通信を許可します。|
    |プライベート|では、同じ Hyper-v サーバー上の仮想マシン間の通信のみが許可されます。 プライベートネットワークは、Hyper-v サーバー上のすべての外部ネットワークトラフィックから分離されます。 この種類のネットワークは、分離されたテストドメインのように、分離されたネットワーク環境を作成する必要がある場合に便利です。|

4.  [ **仮想スイッチの作成**] を選択します。

5.  仮想スイッチの名前を追加します。

6.  [外部] を選択した場合は、使用するネットワークアダプター (NIC) と、次の表に記載されているその他のオプションを選択します。

    ![外部ネットワークオプションを示すスクリーンショット](../media/Hyper-V-NewVSwitch-ExternalOptions.png)

    |設定名|説明|
    |----------------|---------------|
    |管理オペレーティング システムにこのネットワーク アダプターの共有を許可する|仮想スイッチ、NIC、または NIC チームの使用を Hyper-v ホストが仮想マシンと共有できるようにする場合は、このオプションを選択します。 これを有効にすると、ホストは、サービスの品質 (QoS) 設定、セキュリティ設定、または Hyper-v 仮想スイッチのその他の機能など、仮想スイッチに構成した設定のいずれかを使用できます。|
    |シングル ルート I/O 仮想化 (SR-IOV) を有効にする|このオプションは、仮想マシンのトラフィックが仮想マシンのスイッチをバイパスして物理 NIC に直接移動できるようにする場合にのみ選択します。 詳細については、「ポスターネットワーク」の「ポスターの [I/o 仮想化](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn641211(v=ws.11)#Sec4) 」を参照してください。|

7.  管理 Hyper-v ホストオペレーティングシステムまたは同じ仮想スイッチを共有する他の仮想マシンからネットワークトラフィックを分離する場合は、[ **管理オペレーティングシステムの仮想 LAN id を有効に** する] を選択します。 VLAN ID は任意の数に変更することも、既定のままにすることもできます。 これは、管理オペレーティングシステムがこの仮想スイッチ経由のすべてのネットワーク通信に使用する仮想 LAN 識別番号です。

    ![VLAN ID オプションを示すスクリーンショット](../media/Hyper-V-NewSwitch-VLAN.png)

8.  **[OK]** をクリックします。

9. **[はい]** をクリックします。

    !["保留中の変更によりネットワーク接続が中断される可能性がある" というメッセージを示すスクリーンショット](../media/Hyper-V-NewVSwitch-DisruptNetwork.png)

## <a name="create-a-virtual-switch-by-using-windows-powershell"></a>Windows PowerShell を使用して仮想スイッチを作成する

1.  Windows デスクトップで [スタート] ボタンをクリックし、名前の一部を入力 **Windows PowerShell** します。

2.  [Windows PowerShell] を右クリックし、[ **管理者として実行**] を選択します。

3.  [Get NetAdapter](https://technet.microsoft.com/library/jj130867.aspx)コマンドレットを実行して、既存のネットワークアダプターを検索します。 仮想スイッチに使用するネットワークアダプターの名前をメモしておきます。

    ```
    Get-NetAdapter
    ```

4.  [新しい-VMSwitch](/powershell/module/hyper-v/new-vmswitch)コマンドレットを使用して仮想スイッチを作成します。 たとえば、ExternalSwitch という名前の外部仮想スイッチを作成し、イーサネットネットワークアダプターを使用して、[ **管理オペレーティングシステムによるこのネットワークアダプターの共有を許可する** ] がオンになっている場合は、次のコマンドを実行します。

    ```
    New-VMSwitch -name ExternalSwitch  -NetAdapterName Ethernet -AllowManagementOS $true
    ```

    内部スイッチを作成するには、次のコマンドを実行します。

    ```
    New-VMSwitch -name InternalSwitch -SwitchType Internal
    ```

    プライベートスイッチを作成するには、次のコマンドを実行します。

    ```
    New-VMSwitch -name PrivateSwitch -SwitchType Private
    ```

Windows Server 2016 の強化されたまたは新しい仮想スイッチ機能をカバーする、より高度な Windows PowerShell スクリプトについては、「 [リモートダイレクトメモリアクセスとスイッチ埋め込みチーミング](../../hyper-v-virtual-switch/RDMA-and-Switch-Embedded-Teaming.md)」を参照してください。


## <a name="next-step"></a>次のステップ
[HYPER-V で仮想マシンを作成します。](Create-a-virtual-machine-in-Hyper-V.md)
