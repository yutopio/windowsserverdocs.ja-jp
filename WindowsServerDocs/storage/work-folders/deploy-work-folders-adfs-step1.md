---
description: '詳細については、「AD FS と Web アプリケーションプロキシを使用したワークフォルダーの展開: ステップ1、セットアップ」を参照してください AD FS'
title: 'AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開 - 手順 1: AD FS のセットアップ'
ms.topic: article
manager: klaasl
ms.author: jeffpatt
author: JeffPatt24
ms.date: 10/18/2018
ms.assetid: 938cdda2-f17e-4964-9218-f5868fd96735
ms.openlocfilehash: 0cb9e88455a6c7c1b3d917a8ad839d7f7217a6a3
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97048580"
---
# <a name="deploy-work-folders-with-ad-fs-and-web-application-proxy-step-1-set-up-ad-fs"></a>AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開: 手順 1: AD FS のセットアップ

>適用先:Windows Server (半期チャネル)、Windows Server 2016

このトピックでは、Active Directory フェデレーション サービス (AD FS) と Web アプリケーション プロキシを使用して、ワーク フォルダーを展開する最初の手順について説明します。 このプロセスの他の手順は、次のトピックで確認できます。

-   [AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開: 概要](deploy-work-folders-adfs-overview.md)

-   [AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開: 手順 2、AD FS の構成後の作業](deploy-work-folders-adfs-step2.md)

-   [AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開: 手順 3: ワーク フォルダーのセットアップ](deploy-work-folders-adfs-step3.md)

-   [AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開: 手順 4: Web アプリケーション プロキシのセットアップ](deploy-work-folders-adfs-step4.md)

-   [AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開: 手順 5: クライアントのセットアップ](deploy-work-folders-adfs-step5.md)

> [!NOTE]
>   このセクションで説明する手順は、Windows Server 2019 または Windows Server 2016 環境向けです。 Windows Server 2012 R2 を使用している場合には、[Windows Server 2012 R2 の手順](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn747208(v=ws.11)) に従います。

ワーク フォルダーで使用するための AD FS を設定するには、次の手順を使用します。

## <a name="pre-installment-work"></a>事前 \- 分割作業
この手順を使って設定するテスト環境を、運用環境に変換する予定である場合には、開始する前に次の 2 点を行っておくことを推奨します。

-   AD FS サービスを実行するために使用する、Active Directory ドメイン管理者アカウントをセットアップします。

-   サーバー認証のための SSL (Secure Sockets Layer) サブジェクト代替名 (SAN) の証明書を取得します。 テストの例では自己署名証明書を使用できますが、運用環境用には公的に信頼された証明書を使用します。

それらを取得するには会社のポリシーによっては時間がかかる場合があるため、テスト環境を作成する前に、申請処理を開始しておくことが望ましい場合があります。

証明書はさまざまな商用証明機関 (CA) から購入できます。 Microsoft によって信頼されている CA の一覧は [サポート技術情報の記事 931125](https://support.microsoft.com/kb/931125) から参照できます。 別の方法としては、会社のエンタープライズ CA から証明書を取得できます。

テスト環境では、提供スクリプトの 1 つを使って作成する自己署名証明書を使用できます。

> [!NOTE]
> AD FS は Cryptography Next Generation (CNG) 証明書をサポートしません。つまり、Windows PowerShell のコマンドレット New-SelfSignedCertificate を使用して自己署名証明書を作成することはできません。 ただし、「[AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開](https://techcommunity.microsoft.com/t5/storage-at-microsoft/deploying-work-folders-with-ad-fs-and-web-application-proxy-wap/ba-p/425318)」のブログ記事に含まれている makecert.ps1 スクリプトを使用することができます。 このスクリプトは、 \- AD FS で動作する自己署名証明書を作成し、証明書の作成に必要な SAN 名の入力を求めます。

次に、以下のセクションで説明するインストール前の追加の作業を行います。

### <a name="create-an-ad-fs-self-signed-certificate"></a>AD FS 自己 \- 署名証明書を作成する
AD FS 自己署名証明書を作成するには、次の手順に従います。

1.  「[AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開](https://techcommunity.microsoft.com/t5/storage-at-microsoft/deploying-work-folders-with-ad-fs-and-web-application-proxy-wap/ba-p/425318)」のブログ投稿で提供されているスクリプトをダウンロードし、ファイル makecert.ps1 を AD FS のコンピューターにコピーします。

2.  管理者特権で Windows PowerShell ウィンドウを開きます。

3.  実行ポリシーを、Unrestricted に設定します。

    ```powershell
    Set-ExecutionPolicy –ExecutionPolicy Unrestricted
    ```

4.  スクリプトをコピーしたディレクトリに移動します。

5.  makecert スクリプトを実行します。

    ```powershell
    .\makecert.ps1
    ```

6.  サブジェクトの証明書を変更するようにメッセージが表示されたら、サブジェクトの新しい値を入力します。 この例では、値を「**blueadfs.contoso.com**」とします。

7.  SAN の名前を入力するメッセージが表示されたら、Y キーを押し、次に SAN の名前を一度に 1 つずつ入力します。

    この例では、「**blueadfs.contoso.com**」と入力して Enter キーを押し、次に「**2016-adfs.contoso.com**」と入力して Enter キーを押し、次に「**enterpriseregistration.contoso.com**」と入力して Enter キーを押します。

    すべての SAN の名前を入力したら、空の行で Enter キーを押します。

8.  信頼されたルート証明機関ストアに証明書をインストールするようにメッセージが表示されたら、Y キーを押します。

AD FS 証明書は、次の値を持つ SAN 証明書である必要があります。

-   AD FS サービス名.ドメイン

-   enterpriseregistration.ドメイン

-   AD FS サーバー名.ドメイン

テストの例では、値は以下のようになります。

-   **blueadfs.contoso.com**

-   **enterpriseregistration.contoso.com**

-   **2016-adfs.contoso.com**

enterpriseregistration SAN は Workplace Join に必要となります。

### <a name="set-the-server-ip-address"></a>サーバー IP アドレスの設定
サーバーの IP アドレスを静的 IP アドレスに変更します。 テストの例では、IP クラス A を使用し、192.168.0.160 / サブネット マスク: 255.255.0.0 / デフォルト ゲートウェイ: 192.168.0.1 / 優先 DNS: 192.168.0.150 (ドメイン コントローラーの IP アドレス\) とします。

## <a name="install-the-ad-fs-role-service"></a>AD FS 役割サービスをインストールする
AD FS をインストールするには、次の手順に従います。

1.  AD FS をインストールする物理または仮想マシンにログオンして、**サーバー マネージャー** を開き、役割と機能の追加ウィザードを開始します。

2.  **[サーバーの役割]** ページで、**[Active Directory フェデレーション サービス (AD FS)]** の役割を選択し、**[次へ]** をクリックします。

3.  **[Active Directory フェデレーション サービス (AD FS)]** ページで、Web アプリケーション プロキシの役割は AD FS と同じコンピューターにはインストールできないことを示すメッセージが表示されます。 **[次へ]** をクリックします。

4.  確認ページで **[インストール]** をクリックします。

Windows PowerShell を使って AD FS の同等のインストールを行うには、次のコマンドを使用します。

```powershell
Add-WindowsFeature RSAT-AD-Tools
Add-WindowsFeature ADFS-Federation –IncludeManagementTools
```

## <a name="configure-ad-fs"></a>AD FS の構成
次にサーバー マネージャーまたは Windows PowerShell を使って、AD FS を構成します。

### <a name="configure-ad-fs-by-using-server-manager"></a>サーバー マネージャーを使った AD FS の構成
サーバー マネージャーを使って、AD FS を構成するには、次の手順に従います。

1.  サーバー マネージャーを開きます。

2.  サーバー マネージャーのウィンドウの上部にある **[通知]** フラグをクリックし、次に **[このサーバーにフェデレーション サービスを構成します]** をクリックします。

3.  Active Directory フェデレーション サービス (AD FS) 構成ウィザードが起動します。 **[AD DS への接続]** ページで、AD FS アカウントとして使用するドメイン管理者アカウントを入力し、**[次へ]** をクリックします。

4.  **[サービスのプロパティの指定]** ページで、AD FS の通信に使用する SSL 証明書のサブジェクト名を入力します。 このテストの例では、**blueadfs.contoso.com** です。

5.  フェデレーション サービス名を入力します。 このテストの例では、**blueadfs.contoso.com** です。 **[次へ]** をクリックします。

    > [!NOTE]
    > フェデレーション サービス名は、環境内の既存のサーバーの名前を使用しないでください。 既存のサーバーの名前を使う場合、AD FSのインストールは失敗し、再起動する必要があります。

6.  **[サービス アカウントの指定]** ページで、管理されたサービス アカウントとして使用する名前を入力します。 このテストの例では、**[管理されたサービス アカウント グループを作成します]** を選択し、**[アカウント名]** で **「ADFSService」** と入力します。 **[次へ]** をクリックします。

7.  [ **構成データベースの指定** ] ページで、[ **Windows Internal database を使用してこのサーバーにデータベースを作成する**] を選択し、[ **次へ**] をクリックします。

8.  **[オプションの確認]** ページでは、選択したオプションの概要が表示されます。 **[次へ]** をクリックします。

9. **[前提条件の確認]** ページでは、すべての前提条件が確認されたかどうかを示します。 問題がない場合、**[構成]** をクリックします。

    > [!NOTE]
    > AD FS サーバーの名前または他の既存のコンピューターの名前をフェデレーション サービス名に使用した場合、エラー メッセージが表示されます。 イントールをやり直して、既存のコンピューターの名前以外の名前を選択する必要があります。

10. 構成が正常に完了したら、**[結果]** ページで、AD FSが正常に構成されていることを確認します。

### <a name="configure-ad-fs-by-using-powershell"></a>PowerShell を使った AD FS の構成
Windows PowerShell を使って AD FS の同等の構成を行うためには、次のコマンドを使用します。

AD FS をインストールするには:

```powershell
Add-WindowsFeature RSAT-AD-Tools
Add-WindowsFeature ADFS-Federation -IncludeManagementTools
```

管理されたサービス アカウントを作成するには:

```powershell
New-ADServiceAccount "ADFSService"-Server 2016-DC.contoso.com -Path "CN=Managed Service Accounts,DC=Contoso,DC=COM" -DNSHostName 2016-ADFS.contoso.com -ServicePrincipalNames HTTP/2016-ADFS,HTTP/2016-ADFS.contoso.com
```

AD FS を構成した後で、前の手順で作成した管理されたサービス アカウントおよび構成前の手順で作成した証明書を使用して、AD FS ファームをセットアップする必要があります。

AD FS ファームをセットアップするには:

```powershell
$cert = Get-ChildItem CERT:\LocalMachine\My |where {$_.Subject -match blueadfs.contoso.com} | sort $_.NotAfter -Descending | select -first 1 
$thumbprint = $cert.Thumbprint
Install-ADFSFarm -CertificateThumbprint $thumbprint -FederationServiceDisplayName "Contoso Corporation" –FederationServiceName blueadfs.contoso.com -GroupServiceAccountIdentifier contoso\ADFSService$ -OverwriteConfiguration -ErrorAction Stop
```

次の手順: [AD FS と Web アプリケーション プロキシを使ったワーク フォルダーの展開: 手順 2、AD FS の構成後の作業](deploy-work-folders-adfs-step2.md)

## <a name="see-also"></a>関連項目
[ワーク フォルダーの概要](Work-Folders-Overview.md)

