---
title: Windows Admin Center の既知の問題
description: Windows Admin Center の既知の問題 (Project Honolulu)
ms.topic: article
author: jwwool
ms.author: jeffrew
ms.localizationpriority: medium
ms.date: 06/07/2019
ms.openlocfilehash: c062531e96e12ca73e001018ac3f640e27fdad99
ms.sourcegitcommit: f89639d3861c61620275c69f31f4b02fd48327ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/29/2020
ms.locfileid: "91517558"
---
# <a name="windows-admin-center-known-issues"></a>Windows Admin Center の既知の問題

> 適用先:Windows Admin Center、Windows Admin Center Preview

このページで説明されている問題が発生した場合は、[お知らせください](https://aka.ms/WACfeedback)。

## <a name="installer"></a>Installer

- 独自の証明書を使用して Windows Admin Center をインストールする場合は、証明書マネージャー MMC ツールから拇印をコピーすると、[先頭に無効な文字が含まれる](https://support.microsoft.com/help/2023835/certificate-thumbprint-displayed-in-mmc-certificate-snap-in-has-extra)ことに留意してください。 この問題を回避するには、拇印の最初の文字を入力し、残りをコピー/貼り付けします。

- 1024未満のポートの使用はサポートされていません。 サービスモードでは、必要に応じて、指定したポートにリダイレクトするようにポート80を構成できます。

## <a name="general"></a>全般

- Windows 管理センターの1910.2 リリースでは、特定のハードウェア上の Hyper-v サーバーに接続できない場合があります。 この問題でブロックされている場合は、 [以前のビルドをダウンロードしてください](https://aka.ms/wacprevious)。

- Windows **Server 2016** にゲートウェイとしてインストールされている Windows 管理センターを使用している場合、サービスがとを含むイベントログのエラーでクラッシュすることがあり ```Faulting application name: sme.exe``` ```Faulting module name: WsmSvc.dll``` ます。 これは、Windows Server 2019 で修正されたバグが原因です。 Windows Server 2016 の修正プログラムには、2019の累積的な更新プログラム [KB4480977](https://www.catalog.update.microsoft.com/Search.aspx?q=4480977)が含まれています。

- Windows 管理センターがゲートウェイとしてインストールされていて、接続リストが破損していると思われる場合は、次の手順を実行します。

   > [!WARNING]
   >これにより、ゲートウェイのすべての Windows 管理センターユーザーの接続リストと設定が削除されます。

  1. Windows Admin Center をアンインストールします
  2. **C:\Windows\ServiceProfiles\NetworkService\AppData\Roaming\Microsoft** にある **Server Management Experience** フォルダーを削除します
  3. Windows Admin Center を再インストールします

- ツールを開いたまま長時間アイドル状態にすると、**Error: The runspace state is not valid for this operation** (エラー: この操作の実行空間の状態が有効ではありません) というエラーが何度か表示されることがあります。 この問題が発生した場合は、お使いのブラウザーを更新してください。 この問題が発生した場合は、 [フィードバックをお送り](https://aka.ms/WACfeedback)ください。

- Windows 管理センターのモジュールで実行されている OSS のバージョン番号と、サードパーティのソフトウェアに関する通知に記載されているものとの間には、若干の差異がある場合があります。

### <a name="extension-manager"></a>拡張機能マネージャー

- Windows 管理センターを更新する場合は、拡張機能を再インストールする必要があります。
- アクセスできない拡張機能フィードを追加すると、警告は表示されません。 [14412861]

## <a name="browser-specific-issues"></a>ブラウザーに固有の問題

### <a name="microsoft-edge"></a>Microsoft Edge

- Windows 管理センターがサービスとして展開されていて、ブラウザーとして Microsoft Edge を使用している場合は、新しいブラウザーウィンドウを起動した後にゲートウェイを Azure に接続できないことがあります。 この問題を回避するに https://login.microsoftonline.com は、 https://login.live.com ゲートウェイの URL を信頼済みサイトとして追加し、クライアント側ブラウザーでポップアップブロックの設定に許可されたサイトを追加します。 この問題を解決する方法については、 [トラブルシューティングガイド](troubleshooting.md#azure-features-dont-work-properly-in-edge)を参照してください。 [17990376]

### <a name="google-chrome"></a>Google Chrome

- バージョン70より前 (10 月、2018)、Chrome には Websocket プロトコルと NTLM 認証に関する [バグ](https://bugs.chromium.org/p/chromium/issues/detail?id=423609) がありました。 これは、イベント、PowerShell、リモート デスクトップのツールに影響します。

- Chrome では、特に**ワークグループ** (非ドメイン) 環境での接続の追加エクスペリエンスの実行中に、複数の資格情報プロンプトが表示される場合があります。

- Windows 管理センターがサービスとしてデプロイされている場合、Azure 統合機能を使用するには、ゲートウェイ URL のポップアップを有効にする必要があります。

### <a name="mozilla-firefox"></a>Mozilla Firefox

Windows Admin Center は、Mozilla Firefox でテストされていませんが、ほとんどの機能は機能します。

- Windows 10 のインストール: Mozilla Firefox には独自の証明書ストアがあるため、 ```Windows Admin Center Client``` windows 10 で Windows 管理センターを使用するには、Firefox に証明書をインポートする必要があります。

## <a name="websocket-compatibility-when-using-a-proxy-service"></a>プロキシ サービスを使用する場合の WebSocket の互換性

Windows Admin Center のリモート デスクトップ、PowerShell、およびイベント モジュールでは、WebSocket プロトコルを利用します。多くの場合、このプロトコルはプロキシ サービスを使用するときにサポートされていません。

## <a name="support-for-windows-server-versions-before-2016-2012-r2-2012-2008-r2"></a>2016より前の Windows Server バージョンのサポート (2012 R2、2012、2008 R2)

> [!NOTE]
> Windows 管理センターには、Windows Server 2012 R2、2012、または 2008 R2 に含まれていない PowerShell 機能が必要です。 Windows 管理センターで Windows Server を管理する場合は、これらのサーバーに WMF バージョン5.1 以上をインストールする必要があります。

PowerShell で `$PSVersiontable` を入力して、WMF がインストールされていること、またバージョンが 5.1 以上であることを確認します。

インストールされていない場合は、[WMF 5.1 をダウンロードしてインストール](https://www.microsoft.com/download/details.aspx?id=54616)できます。

## <a name="role-based-access-control-rbac"></a>ロールベースの Access Control (RBAC)

- Windows Defender アプリケーション制御 (WDAC、旧称はコードの整合性) を使用するように構成されているコンピューターでは、RBAC 展開は成功しません。[16568455]

- クラスターで RBAC を使用するには、各メンバー ノードに個別に構成を展開する必要があります。

- RBAC が展開されたときに、RBAC 構成に誤って起因する不正なエラーが表示される場合があります。 [16369238]

## <a name="server-manager-solution"></a>サーバー マネージャー ソリューション

### <a name="certificates"></a>証明書

- .PFX の暗号化された証明書を現在のユーザー ストアにインポートすることはできません。 [11818622]

### <a name="events"></a>events

- イベントは、[プロキシ サービスを使用する場合に WebSocket の互換性](#websocket-compatibility-when-using-a-proxy-service)に影響を受けます。

- 大きいログ ファイルをエクスポートするときに、“パケット サイズ” を参照するエラーが表示される場合があります。

  - これを解決するには、ゲートウェイコンピューターで管理者特権のコマンドプロンプトで次のコマンドを使用します。 ```winrm set winrm/config @{MaxEnvelopeSizekb="8192"}```

### <a name="files"></a>Files

- 大きいファイルのアップロードまたはダウンロードはまだサポートされていません。 ( \~ 100mb の制限) [12524234]

### <a name="powershell"></a>PowerShell

- PowerShell は、[プロキシ サービスを使用する場合に WebSocket の互換性](#websocket-compatibility-when-using-a-proxy-service)に影響を受けます。

- デスクトップの PowerShell コンソールと同じように 1 回の右クリックで貼り付けしても機能しません。 代わりに、ブラウザーのコンテキスト メニューが表示され、ここで貼り付けを選択できます。 Ctrl + V も機能します。

- Ctrl + C によるコピーは機能しません。常に Ctrl-C Break コマンドがコンソールに送信されます。 右クリックすると表示されるコンテキスト メニューからのコピーは機能します。

- Windows Admin Center のウィンドウを縮小する場合は、端のコンテンツは再配置されますが、もう一度拡大すると、コンテンツは前の状態に戻らないことがあります。 項目が乱雑になる場合は、Clear-Host を試すか、端末上にあるボタンを使用して切断および再接続することができます。

### <a name="registry-editor"></a>レジストリ エディター

- 検索機能が実装されていません。 [13820009]

### <a name="remote-desktop"></a>リモート デスクトップ

- Windows 管理センターがサービスとして展開されている場合、Windows 管理センターサービスを新しいバージョンに更新すると、リモートデスクトップツールが読み込みに失敗することがあります。 この問題を回避するには、ブラウザーのキャッシュをクリアします。   [23824194]

- Windows Server 2012 を管理している場合、リモートデスクトップツールが接続に失敗することがあります。 [20258278]

- リモートデスクトップを使用して、ドメインに参加していないコンピューターに接続する場合は、の形式でアカウントを入力する必要があり ```MACHINENAME\USERNAME``` ます。

- 一部の構成では、Windows 管理センターのリモートデスクトップクライアントがグループポリシーでブロックされることがあります。 この問題が発生した場合は、 ```Allow users to connect remotely by using Remote Desktop Services``````Computer Configuration/Policies/Administrative Templates/Windows Components/Remote Desktop Services/Remote Desktop Session Host/Connections```

- リモートデスクトップは websocket 互換性によって影響を受け [ます。](#websocket-compatibility-when-using-a-proxy-service)

- リモート デスクトップ ツールは現在、ローカル デスクトップとリモート セッションの間のテキスト、イメージ、またはファイルのコピー/貼り付けをサポートしていません。

- リモート セッション内でコピー/貼り付けを行うには、通常どおりコピーできます (右クリックによるコピーまたは Ctrl+C) が、貼り付けは、右クリックによる貼り付けをする必要があります (Ctrl+V は機能しません)。

- 次のキーコマンドをリモート セッションに送信することはできません。
  - Alt + Tab
  - ファンクション キー
  - Windows キー
  - PrtScn

### <a name="roles-and-features"></a>役割と機能

- インストールに使用できないソースを含む役割や機能を選択すると、スキップされます。 [12946914]

- 役割のインストール後に自動的に再起動しないように選択すると、今後メッセージは表示されません。 [13098852]

- 自動的に再起動するように選択した場合、状態が 100% に更新される前に、再起動が行われます。 [13098852]

### <a name="storage"></a>ストレージ

- ダウンレベル: DVD/CD/フロッピー ドライブは、ダウンレベルのボリュームとして表示されません。

- ダウンレベル: ボリュームとディスクの一部のプロパティはダウンレベルで利用できないため、詳細パネルで不明または空白で表示されます。

- ダウンレベル: 新しいボリュームを作成する場合、ReFS では、Windows 2012 および 2012 R2 コンピューターでの 64K のアロケーション ユニット サイズのみがサポートされます。 ReFS ボリュームがダウンレベル ターゲットの小さいアロケーション ユニット サイズで作成された場合は、ファイル システムの書式設定が失敗します。 新しいボリュームは使用できません。 解決策は、ボリュームを削除し、64 K のアロケーション ユニット サイズを使用することです。

### <a name="updates"></a>更新プログラム

- 更新プログラムをインストールすると、インストールの状態がキャッシュされ、ブラウザーの更新が必要になる場合があります。

- Azure Update management を設定しようとすると、"キーセットが存在しません" というエラーが発生することがあります。 この場合は、管理ノードで次の修復手順を試してください。
    1. ' Cryptographic Services ' サービスを停止します。
    2. 隠しファイルを表示するようにフォルダーオプションを変更します (必要な場合)。
    3. "%Allusersprofile%\Microsoft\Crypto\RSA\S-1-5-18" フォルダーを受け取って、その内容をすべて削除します。
    4. ' Cryptographic Services ' サービスを再起動してください。
    5. Windows 管理センターで Update Management のセットアップを繰り返す

### <a name="virtual-machines"></a>Virtual Machines

- Windows Server 2012 ホスト上の仮想マシンを管理する場合、ブラウザー内 VM 接続ツールは VM に接続できません。 VM に接続するための .rdp ファイルのダウンロードは引き続き機能します。 [20258278]

- Azure Site Recovery – ASR が WAC の外部のホストにセットアップされている場合、WAC 内から VM を保護することはできません [18972276]

- 仮想 SAN マネージャー、Move VM、Export VM、VM レプリケーションなどの Hyper-V マネージャーで利用可能な高度な機能は、現在サポートされていません。

### <a name="virtual-switches"></a>仮想スイッチ

- スイッチ埋め込みチーミング (SET): NIC をチームに追加する場合は、NIC が同じサブネット上にある必要があります。

## <a name="computer-management-solution"></a>コンピューターの管理ソリューション

コンピューターの管理ソリューションには、サーバー マネージャー ソリューションのツールのサブセットが含まれているため、同じ既知の問題と共に、次のコンピューターの管理ソリューション特有の問題が該当します。

- Microsoft アカウント ([MSA](https://account.microsoft.com/account/)) を使用する場合、または AZURE ACTIVE DIRECTORY (AAD) を使用して Windows 10 コンピューターにログオンする場合は、"manage-as" を使用してローカル管理者アカウントの資格情報を指定する必要があります [16568455]

- ローカル ホストを管理しようとすると、ゲートウェイ プロセスを昇格するように求められます。 次のユーザーアカウント制御ポップアップで [ **いいえ** ] をクリックすると、接続試行を取り消してからやり直す必要があります。

- 既定では、Windows 10 では WinRM と PowerShell のリモート処理が行われません。

  - Windows 10 クライアントの管理を有効にするには、管理者特権の PowerShell プロンプトから ```Enable-PSRemoting``` コマンドを実行する必要があります。

  - また、```Set-NetFirewallRule -Name WINRM-HTTP-In-TCP -RemoteAddress Any``` を使用して、ローカル サブネットの外部から接続を許可できるようにファイアウォールを更新する必要があります。 より制限の厳しいネットワーク シナリオでは、[このドキュメント](/powershell/module/microsoft.powershell.core/enable-psremoting?view=powershell-5.1&preserve-view=true)を参照してください。

## <a name="cluster-deployment"></a>クラスターの展開

### <a name="step-12"></a>手順1.2
サーバーを追加する場合、ワークグループコンピューターが混在していることは現在サポートされていません。 クラスタリングに使用されるすべてのコンピューターは、同じワークグループに属している必要があります。 そうでない場合、[次へ] ボタンは無効になり、"異なる Active Directory ドメインにサーバーを持つクラスターを作成することはできません" というエラーが表示されます。 サーバー名が正しいことを確認します。 すべてのサーバーを同じドメインに移動して、もう一度やり直してください。 "

### <a name="step-14"></a>手順1.4
Hyper-v は、Azure Stack HCI OS を実行する仮想マシンにインストールする必要があります。 これらの仮想マシンに対して Hyper-v 機能を有効にしようとすると、次のエラーが発生して失敗します。

![Hyper-v の有効化エラーのスクリーンショット](../media/cluster-create-install-hyperv.png)

Azure Stack HCI OS を実行している仮想マシンに Hyper-v をインストールするには、次のコマンドを実行します。

```PowerShell
Enable-WindowsOptionalFeature -Online -FeatureName 'Microsoft-Hyper-V'
```

### <a name="step-17"></a>手順1.7
更新プログラムのインストール後に、サーバーの再起動に予想以上に時間がかかることがあります。 Windows 管理センターのクラスター展開ウィザードは、サーバーが正常に再起動されたかどうかを確認するために、サーバーの再起動状態を定期的に確認します。 ただし、ユーザーがウィザードの外部でサーバーを手動で再起動した場合、ウィザードに適切な方法でサーバーの状態をキャプチャする方法はありません。

サーバーを手動で再起動する場合は、現在のウィザードセッションを終了します。 サーバーを再起動した後、ウィザードを再起動することができます。

### <a name="stretch-cluster-creation"></a>ストレッチクラスターの作成
ストレッチクラスターを作成するときは、ドメインに参加しているサーバーを使用することをお勧めします。 WinRM の制限により、ストレッチクラスターの展開にワークグループコンピューターを使用しようとすると、ネットワークセグメント化の問題が発生します。

### <a name="undo-and-start-over"></a>元に戻すとやり直す
クラスターのデプロイに同じマシンを繰り返し使用する場合、以前のクラスターエンティティのクリーンアップは、同じマシンセットでクラスターのデプロイを成功させるために重要です。 クラスターをクリーンアップする方法については、 [ハイパー集約型インフラストラクチャの展開](../use/deploy-hyperconverged-infrastructure.md#undo-and-start-over) に関するページを参照してください。

### <a name="credssp"></a>CredSSP
Windows 管理センターのクラスター展開ウィザードでは、いくつかの場所で CredSSP が使用されます。 ウィザードの実行中にこのエラーメッセージが表示されます (これは、クラスターの検証手順で最も頻繁に発生します)。

![クラスター作成 CredSSP エラーのスクリーンショット](../media/cluster-create-credssp-error.jpg)

次の手順を使用して、トラブルシューティングを行うことができます。

1. すべてのノードと Windows 管理センターゲートウェイコンピューターの CredSSP 設定を無効にします。 ゲートウェイコンピューターで最初のコマンドを実行し、クラスター内のすべてのノードで2番目のコマンドを実行します。

```PowerShell
Disable-WsmanCredSSP -Role Client
```
```PowerShell
Disable-WsmanCredSSP -Role Server
```
2. すべてのノードで信頼を修復してください。 すべてのノードで次のコマンドを実行します。
```PowerShell
Test-ComputerSecureChannel -Verbose -Repair -Credential <account name>
```

3. コマンドを使用してグループポリシーの伝達されたデータをリセットする
```Command Line
gpupdate /force
```

4. ノードを再起動します。 再起動後、次のコマンドを使用して、ゲートウェイコンピューターとターゲットノードの間の接続と、ノード間の接続をテストします。
```PowerShell
Enter-PSSession -computername <node fqdn>
```

### <a name="nested-virtualization"></a>入れ子になった仮想化
仮想マシン上で Azure Stack HCI OS クラスターの展開を検証するときは、次の powershell コマンドを使用して、役割/機能が有効になる前に、入れ子になった仮想化を有効にする必要があります。

```PowerShell
Set-VMProcessor -VMName <VMName> -ExposeVirtualizationExtensions $true
```

  > [!Note]
  > 仮想マシン環境で仮想スイッチのチーミングを成功させるには、仮想マシンの作成後すぐに、次のコマンドを PowerShell で実行する必要があります。% {VMNetworkAdapter-VMName $ _.Name-MacAddressSpoofing On-AllowTeaming on}

Azure Stack HCI OS を使用してクラスターをデプロイする場合は、追加の要件があります。 VM ブート仮想ハードドライブは、Hyper-v 機能と共にプレインストールされている必要があります。 これを行うには、仮想マシンを作成する前に次のコマンドを実行します。

```PowerShell
Install-WindowsFeature –VHD <Path to the VHD> -Name Hyper-V, RSAT-Hyper-V-Tools, Hyper-V-PowerShell
```

### <a name="support-for-rdma"></a>RDMA のサポート
Windows 管理センターバージョン2007のクラスター展開ウィザードでは、RDMA の構成はサポートされていません。

## <a name="failover-cluster-manager-solution"></a>フェールオーバー クラスター マネージャー ソリューション

- クラスター (ハイパーコンバージドまたは従来のクラスターのいずれか) を管理するときに、**shell was not found** (シェルが見つかりませんでした) というエラーが発生する場合があります。 この問題が発生した場合は、お使いのブラウザーを再読み込みするか、別のツールに移動して戻ります。 [13882442]

- 完全に構成されていない下位バージョン (Windows Server 2012 または 2012 R2) のクラスターを管理するときに問題が発生することがあります。 この問題の解決方法は、Windows の機能**RSAT クラスタ リング PowerShell**がインストールされ、クラスターの**各メンバー ノード**で有効になっていることを確認することです。 PowerShell でこれを行うには、すべてのクラスター ノードで `Install-WindowsFeature -Name RSAT-Clustering-PowerShell` コマンドを入力します。 [12524664]

- クラスターは正しく検出されるように全 FQDN を指定して追加する必要があります。

- ゲートウェイとしてインストールされた Windows Admin Center を使用してクラスターに接続する場合は、メンバー ノードを照会するために資格情報を利用できるように、**Use these credentials for all connections** (これらの資格情報をすべての接続に使用する) を選択する必要があります。

## <a name="hyper-converged-cluster-manager-solution"></a>ハイパーコンバージド クラスター マネージャー ソリューション

- **Drives - Update firmware**、**Servers - Remove**、および **Volumes - Open** などの一部のコマンドは無効になっていて現在サポートされていません。

## <a name="azure-services"></a>Azure サービス

### <a name="azure-login-and-gateway-registration"></a>Azure のログインとゲートウェイの登録
2009リリースでは、Azure へのログインまたは Windows 管理センターゲートウェイの Azure への登録に関する問題が発生する可能性があります。 以下のガイダンスは、これらの問題を軽減するのに役立ちます。 

* ゲートウェイの登録を含め、Windows 管理センター内で Azure の機能を使用する前に、別のタブまたはウィンドウで Azure アカウントにサインインしていることを確認してください。 [Azure ポータル](https://portal.azure.com/)を使用してサインインすることをお勧めします。  

* ゲートウェイの登録中に Azure に正常にサインインしても、Windows 管理センターの設定の [ **azure** ] ページで [視覚的な確認] が表示されない場合は、 **azure** ページに戻る前に、[設定] の別のページに移動してみてください。 

* このビルドでは、Azure サインインのポップアップがより頻繁に表示される場合があり、管理者が Windows 管理センターのアクセス許可をより頻繁に付与することが必要になる場合があります。 

* Azure Portal で Windows 管理センターの管理者の承認を既に付与していても、"管理者の承認が必要" というエラーメッセージが表示される場合は、[ **設定** ] ページではなく、Windows 管理センターのいずれかのバナーを使用して Azure にサインインしてみてください。 

### <a name="azure-file-sync-permissions"></a>Azure File Sync のアクセス許可

Azure File Sync には、Windows 管理センターがバージョン1910より前に提供していない Azure のアクセス許可が必要です。 Windows 管理センターのバージョン1910より前のバージョンを使用して Windows 管理センターゲートウェイを Azure に登録した場合は、Azure Active Directory アプリケーションを更新して、最新バージョンの Windows 管理センターで Azure File Sync を使用するための正しいアクセス許可を取得する必要があります。 追加のアクセス許可により、この記事の説明に従って、ストレージアカウントへのアクセスの自動構成を実行 Azure File Sync ことができます。 [Azure File Sync にストレージアカウントへのアクセス権があることを確認](/azure/storage/files/storage-sync-files-troubleshoot?tabs=portal1%2cazure-portal#tabpanel_CeZOj-G++Q-5_azure-portal)してください。

Azure Active Directory アプリを更新するには、次の2つのいずれかを実行します。
1. [**設定**] [  >  **azure**の  >  **登録解除**] の順に選択し、もう一度 Windows 管理センターを Azure に登録して、新しい Azure Active Directory アプリケーションを作成することを確認します。
2. Azure Active Directory アプリケーションにアクセスし、Windows 管理センターに登録されている既存の Azure Active Directory アプリに必要なアクセス許可を手動で追加します。 これを行うには、 **Settings**  >  **Azure**  >  **azure での azure ビューの**設定に関するページを参照してください。 Azure の [ **アプリの登録** ] ブレードで、[API の **アクセス許可**] にアクセスし、[ **アクセス許可の追加**] を選択します。 下にスクロールして **Azure Active Directory グラフ**を選択し、[委任された **アクセス許可**]、[ **ディレクトリ**] の順に展開して、[ **AccessAsUser**] を選択します。 [ **アクセス許可の追加** ] をクリックして、アプリに更新プログラムを保存します。

### <a name="options-for-setting-up-azure-management-services"></a>Azure 管理サービスを設定するためのオプション

Azure Monitor、Azure Update Management、Azure Security Center を含む azure の管理サービスは、オンプレミスのサーバーと同じエージェントを使用します (Microsoft Monitoring Agent)。 Azure Update Management には、サポートされているリージョンのセットが制限されており、Log Analytics ワークスペースが Azure Automation アカウントにリンクされている必要があります。 この制限により、Windows 管理センターで複数のサービスをセットアップする場合は、まず Azure Update Management を設定してから、Azure Security Center または Azure Monitor する必要があります。 Microsoft Monitoring Agent を使用する Azure 管理サービスを構成した後、Windows 管理センターを使用して Azure Update Management を設定しようとすると、Windows 管理センターでは、Microsoft Monitoring Agent にリンクされている既存のリソースが Azure Update Management をサポートしている場合にのみ Azure Update Management を構成できます。 そうでない場合は、次の2つのオプションがあります。

1. [コントロールパネル] > Microsoft Monitoring Agent を選択し [て、既存の Azure 管理ソリューション](/azure/azure-monitor/platform/log-faq#q-how-do-i-stop-an-agent-from-communicating-with-log-analytics) (Azure Monitor や Azure Security Center など) からサーバーを切断します。 次に、Windows 管理センターで Azure Update Management を設定します。 その後、Windows 管理センターを使用して、問題なく他の Azure 管理ソリューションを設定することができます。
2. [Azure Update Management に必要な azure リソースを手動で設定](/azure/automation/automation-update-management)し、Microsoft Monitoring Agent (Windows 管理センターの外部) を[手動で更新](/azure/azure-monitor/platform/agent-manage#adding-or-removing-a-workspace)して、使用する Update Management ソリューションに対応する新しいワークスペースを追加することができます。
