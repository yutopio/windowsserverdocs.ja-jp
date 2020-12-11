---
description: 詳細については、「フェデレーションサーバーを構成する」を参照してください。
ms.assetid: 434fd617-373a-405e-bae4-da324ea83efc
title: Windows Server 2012 R2 のフェデレーションサーバーを構成する AD FS
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 28a9ad04e1457ac7916cd0092eb53d80a2b57e6f
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97044250"
---
# <a name="configure-a-federation-server"></a>フェデレーション サーバーを構成する


\(コンピューターに Active Directory フェデレーションサービス (AD FS) AD FS 役割サービスをインストールすると \) 、このコンピューターをフェデレーションサーバーになるように構成することができます。 次のいずれかの手順を行います。

-   [新しいフェデレーションサーバー ファームでの最初のフェデレーション サーバーの構成](Configure-a-Federation-Server.md#configure-the-first-federation-server-in-a-new-federation-server-farm)

-   [フェデレーション サーバーを既存のフェデレーション サーバー ファームに追加する](Configure-a-Federation-Server.md#add-a-federation-server-to-an-existing-federation-server-farm)

## <a name="configure-the-first-federation-server-in-a-new-federation-server-farm"></a>新しいフェデレーションサーバー ファームでの最初のフェデレーション サーバーの構成

### <a name="to-configure-the-first-federation-server-in-a-new-federation-server-farm-by-using-the-active-directory-federation-service-configuration-wizard"></a>Active Directory フェデレーションサービス構成ウィザードを使用して、新しいフェデレーションサーバーファームの最初のフェデレーションサーバーを構成するには

> [!NOTE]
> この手順を実行する前に、ドメイン管理者のアクセス許可があること、またはドメイン管理者の資格情報が使用可能であることを確認してください。

1.  Server Manager の [**ダッシュボード**] ページで、[**通知**] フラグをクリックし、[**サーバーにフェデレーション サービスを構成します**] をクリックします。

    **Active Directory フェデレーション サービス構成ウィザード** が開きます。

2.  **[ようこそ]** ページで、**[フェデレーション サーバー ファームに最初のフェデレーション サーバーを作成します]** を選択し、**[次へ]** をクリックします。

3.  [ **AD DS への接続** ] ページで、このコンピューターが参加している Active Directory AD ドメインのドメイン管理者アクセス許可を使用してアカウントを指定 \( し、 \) [ **次へ**] をクリックします。

4.  **[サービスのプロパティの指定]** ページで次の操作を実行してから、**[次へ]** をクリックします。

    -   前の手順で取得した Secure Socket Layer \( SSL \) 証明書とキーを含む .pfx ファイルをインポートします。 [「手順 2: AD FS の SSL 証明書を登録](../../ad-fs/deployment/Enroll-an-SSL-Certificate-for-AD-FS.md)する」では、この証明書を取得し、フェデレーションサーバーとして構成するコンピューターにコピーしました。 ウィザードを使用して .pfx ファイルをインポートするには、[ **インポート**] をクリックし、ファイルの場所を参照します。 メッセージが表示されたら、.pfx ファイルのパスワードを入力します。

    -   フェデレーション サービスの名前を入力します。 たとえば **fs.contoso.com** などです。 この名前は、証明書の件名、またはサブジェクト代替名のいずれかと一致する必要があります。

    -   フェデレーション サービスの表示名を入力します。 たとえば **Contoso Corporation** などです。 ユーザーには、Active Directory フェデレーションサービス (AD FS) AD FS サインインページでこの名前が表示さ \( \) \- れます。

5.  **[サービス アカウントの指定]** ページで、サービス アカウントを指定します。 既存のグループの管理されたサービスアカウント gMSA を作成または使用するか、 \( 既存のドメインユーザーアカウントを使用することができ \) ます。 新しい gMSA アカウントを作成するオプションを選択した場合は、新しいアカウントの名前を指定します。 既存の gMSA アカウントまたはドメインアカウントを使用するオプションを選択した場合は、[ **選択** ] をクリックしてアカウントを選択します。

    > [!NOTE]
    > GMSA アカウントを使用する利点は、自動 \- ネゴシエートパスワード更新機能です。

    > [!WARNING]
    > GMSA アカウントを使用する場合は、Windows Server 2012 オペレーティングシステムを実行している環境内に少なくとも1つのドメインコントローラーが必要です。
    >
    > GMSA オプションが無効になっていて、 **KDS ルートキーが設定されていないためにグループの管理されたサービスアカウントが使用できない** などのエラーメッセージが表示される場合は、Active Directory ドメインで windows Server 2012 以降を実行しているドメインコントローラーで次の windows PowerShell コマンドを実行して、ドメインで gMSA を有効にできます `Add-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)` 。 ウィザードに戻り、[ **前** へ] をクリックし、[ **次へ** ] をクリックして [ \- **サービスアカウントの指定** ] ページに戻ります。 GMSA オプションが有効になります。 これを選択し、使用する gMSA アカウント名を入力できます。

6.  [ **構成データベースの指定** ] ページで、AD FS 構成データベースを指定し、[ **次へ**] をクリックします。 Windows Internal Database WID を使用してこのコンピューターにデータベースを作成するか、 \( \) Microsoft SQL Server の場所とインスタンス名を指定することができます。

    詳細については、「[AD FS 構成データベースの役割](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)」を参照してください。

    > [!IMPORTANT]
    > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2008 以降のバージョン (SQL Server 2012 や SQL Server 2014 を含む) を使用できます。

7.  **[オプションの確認]** ページで、構成の選択内容を確認し、**[次へ]** をクリックします。

8.  [前提 **\- 条件チェック** の実行] ページで、すべての前提条件の確認が正常に完了したことを確認し、[ **構成**] をクリックします。

9. [ **結果** ] ページで結果を確認し、構成が正常に完了したかどうかを確認して、[ **フェデレーションサービスの展開を完了するために必要な次の手順**] をクリックします。 詳細については、「 [AD FS のインストールを完了するための次の手順](https://go.microsoft.com/fwlink/p/?LinkId=286704)」を参照してください。 **[閉じる]** をクリックしてウィザードを終了します。

### <a name="to-configure-the-first-federation-server-in-a-new-federation-server-farm-via-windows-powershell"></a>Windows PowerShell を使って、新しいフェデレーションサーバー ファームで最初のフェデレーション サーバーを構成するには
新規または既存の gMSA アカウントまたは既存のドメインユーザーアカウントのいずれかを使用して、新しいフェデレーションサーバーファームを作成できます。

-   **新しい gMSA アカウントを使用して新しいフェデレーションサーバーを作成する場合は、次の手順を実行します。**

    > [!IMPORTANT]
    > 新しいフェデレーション サーバー ファームで、最初のフェデレーション サーバーを作成するには、ドメイン管理者権限が必要です。

    1.  フェデレーションサーバーとして構成するコンピューターで、必要な SSL 証明書が **ローカルコンピューターの \\ My Store** ディレクトリにインポートされていることを確認します。 Windows PowerShell コマンドウィンドウで次のコマンドを実行して、SSL 証明書がインポートされているかどうかを確認 `dir Cert:\LocalMachine\My` できます。 証明書は、 **ローカルコンピューターの \\ My Store** ディレクトリにある拇印によって一覧表示されます。

    2.  ドメインコントローラーで、Windows PowerShell コマンドウィンドウを開き、次のコマンドを実行して、KDS ルートキーがドメインに作成されているかどうかを確認します `Get-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)` 。 出力に情報が表示されないように作成されていない場合は、次のコマンドを実行してキーを作成し `Add-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)` ます。

    3.  フェデレーション サーバーとして構成するコンピューターで、Windows PowerShell コマンド ウィンドウを開き、次のコマンドを実行します。

        ```
        Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -GroupServiceAccountIdentifier <domain>\<GMSA_Name>$
        ```

        > [!WARNING]
        > `$`前のコマンドの最後にある符号が必要です。

        の値を取得するには、 `<certificate_thumbprint>` を実行し、 `dir Cert:\LocalMachine\My` SSL 証明書の拇印を選択します。 `<federation_service_name>` の値はフェデレーション サーバーの名前で、**fs.contoso.com** などです。

        > [!NOTE]
        > このコマンドを初めて実行する場合は、パラメーターを追加し `OverwriteConfiguration` ます。

        > [!NOTE]
        > 前のコマンドは、WID ファームを作成します。 SQL Server サーバーファームを作成する場合は、SQL Server のインスタンスが既にインストールされ、動作している必要があります。
        >
        > 次のコマンドを使用すると、SQL Server のインスタンスを使用する新しいファームに最初のフェデレーションサーバーを作成できます。 `Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -SQLConnectionString "Data Source=<SQL_Host_Name?\<SQL_instance_ name>;Integrated Security=True"` **<sql \_ ホスト \_ 名>** は SQL Server を実行しているサーバーの名前、<**sql \_ インスタンス \_ 名**>は SQL Server のインスタンスの名前です。 SQL Server の既定のインスタンスを使用する場合は、 **Sqlconnectionstring** 値として "**データソース \=<SQL \_ ホスト \_ 名>; 統合セキュリティ \= True**" を使用します。

        > [!IMPORTANT]
        > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2012 など、SQL Server 2008 以降のバージョンを使用できます。

-   **既存のドメインユーザーアカウントを使用して新しいフェデレーションサーバーを作成する場合は、次の手順を実行します。**

    1.  フェデレーションサーバーとして構成するコンピューターで、必要な SSL 証明書が **ローカルコンピューターの \\ My Store** ディレクトリにインポートされていることを確認します。 Windows PowerShell コマンドウィンドウで次のコマンドを実行して、SSL 証明書がインポートされているかどうかを確認 `dir Cert:\LocalMachine\My` できます。 証明書は、 **ローカルコンピューターの \\ My Store** ディレクトリにある拇印によって一覧表示されます。

    2.  フェデレーションサーバーとして構成するコンピューターで、Windows PowerShell コマンドウィンドウを開き、コマンドを実行し `$fscred = Get-Credential` ます。 ドメインユーザー名の形式で、フェデレーションサービスアカウントに使用するドメインユーザーアカウントの資格情報を入力し \\ ます。

    3.  同じ Windows PowerShell コマンド ウィンドウで、次のコマンドを実行します。

        ```
        Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -ServiceAccountCredential $fscred
        ```

        **<証明書の \_ 拇印>** の値を取得するには、 `dir Cert:\LocalMachine\My` を実行し、SSL 証明書の拇印を選択します。 **<フェデレーション \_ サービス \_ 名>** の値は、フェデレーションサービスの名前です。たとえば、fs.contoso.com のようになります。

        > [!NOTE]
        > このコマンドを初めて実行する場合は、パラメーターを追加し `OverwriteConfiguration` ます。

        > [!NOTE]
        > 前のコマンドは、WID ファームを作成します。 SQL Server ファームを作成する場合は、SQL Server のインスタンスが既にインストールされ、動作している必要があります。
        >
        > 次のコマンドを使用して、SQL Server のインスタンスを使用する新しいファームに最初のフェデレーションサーバーを作成できます。ここで、 `Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -ServiceAccountCredential $fscredential -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` **sql \_ ホスト \_ 名** は SQL Server を実行しているサーバーの名前、 **sql \_ インスタンス \_ 名** は SQL Server のインスタンスの名前です。 SQL Server の既定のインスタンスを使用する場合は、 **Sqlconnectionstring** 値として "**データソース \=<SQL \_ ホスト \_ 名>; 統合セキュリティ \= True**" を使用します。

        > [!IMPORTANT]
        > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2008 以降のバージョン (SQL Server 2012 や SQL Server 2014 を含む) を使用できます。

## <a name="add-a-federation-server-to-an-existing-federation-server-farm"></a>フェデレーション サーバーを既存のフェデレーション サーバー ファームに追加する

> [!IMPORTANT]
> このセクションの手順を開始する前に、「 [手順 3: AD FS の役割サービスをインストール](../../ad-fs/deployment/Install-the-AD-FS-Role-Service.md)する」を完了していることを確認します。

> [!IMPORTANT]
> この手順を実行する前に、有効な SSL サーバー認証証明書を取得していることを確認してください。

### <a name="to-add-a-federation-server-to-an-existing-federation-server-farm-via-the-active-directory-federation-service-configuration-wizard"></a>Active Directory フェデレーション サービス構成ウィザードを使って、フェデレーション サーバーを既存のフェデレーション サーバー ファームに追加するには

1.  Server Manager の [**ダッシュボード**] ページで、[**通知**] フラグをクリックし、[**サーバーにフェデレーション サービスを構成します**] をクリックします。

    **Active Directory フェデレーション サービス構成ウィザード** が開きます。

2.  [ **ようこそ** ] ページで、[フェデレーションサーバー **ファームにフェデレーションサーバーを追加する**] を選択し、[ **次へ**] をクリックします。

3.  [ **AD DS への接続** ] ページで、このコンピューターが参加している AD ドメインのドメイン管理者アクセス許可を使用してアカウントを指定し、[ **次へ**] をクリックします。

4.  [ **ファームの指定** ] ページで、WID を使用するファーム内のプライマリフェデレーションサーバーの名前を指定するか、SQL Server を使用する既存のフェデレーションサーバーファームのデータベースホスト名とデータベースインスタンス名を指定します。

    > [!WARNING]
    > Windows Server &reg; 2012 R2 では、SQL Server の既定のインスタンスを指定するための回避策があります。 この回避策ではユーザー インターフェイスは使用しません。 代わりに、「」の手順に従って、Windows PowerShell を使用して [新しいフェデレーションサーバーファームの最初のフェデレーションサーバーを構成](Configure-a-Federation-Server.md#BKMK_3)します。

    > [!IMPORTANT]
    > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2012 など、SQL Server 2008 以降のバージョンを使用できます。

5.  [ **Ssl 証明書の指定** ] ページで、以前に取得した ssl 証明書とキーを含む .pfx ファイルをインポートします。 この証明書は必須のサービス認証証明書です。 [「手順 2: AD FS の SSL 証明書を登録](../../ad-fs/deployment/Enroll-an-SSL-Certificate-for-AD-FS.md)する」では、この証明書を取得し、フェデレーションサーバーとして構成するコンピューターにコピーしました。 ウィザードを使用して .pfx ファイルをインポートするには、[ **インポート** ] をクリックし、ファイルの場所を参照します。 メッセージが表示されたら、.pfx ファイルのパスワードを入力します。

6.  [ **サービスアカウントの指定** ] ページで、ファームに最初のフェデレーションサーバーを作成したときに構成したものと同じサービスアカウントを指定します。 既存のグループ Managed Service Account や既存のドメイン ユーザー アカウントを使用することもできます。

    > [!IMPORTANT]
    > 指定するアカウントは、このファームのプライマリフェデレーションサーバーで使用されていたアカウントと同じアカウントである必要があります。

7.  **[オプションの確認]** ページで、構成の選択内容を確認し、**[次へ]** をクリックします。

8.  [前提 **\- 条件チェック** の実行] ページで、すべての前提条件の確認が正常に完了したことを確認し、[ **構成**] をクリックします。

9. [ **結果** ] ページで結果を確認し、構成が正常に完了したかどうかを確認して、[ **フェデレーションサービスの展開を完了するために必要な次の手順**] をクリックします。 詳細については、「 [AD FS のインストールを完了するための次の手順](https://go.microsoft.com/fwlink/p/?LinkId=286704)」を参照してください。 **[閉じる]** をクリックしてウィザードを終了します。

### <a name="to-add-a-federation-server-to-an-existing-federation-server-farm-via-windows-powershell"></a>Windows PowerShell を介して、フェデレーション サーバーを既存のフェデレーション サーバー ファームに追加するには
既存の gMSA アカウントまたは既存のドメインユーザーアカウントを使用して、既存のファームにフェデレーションサーバーを追加できます。

-   既存の gMSA アカウントを使用してフェデレーションサーバーをファームに参加させる場合は、次の手順を実行します。

    1.  フェデレーションサーバーとして構成するコンピューターで、必要な SSL 証明書が **ローカルコンピューターの \\ My Store** ディレクトリにインポートされていることを確認します。 Windows PowerShell コマンドウィンドウで次のコマンドを実行して、SSL 証明書がインポートされているかどうかを確認 `dir Cert:\LocalMachine\My` できます。 証明書は、 **ローカルコンピューターの \\ My Store** ディレクトリにある拇印によって一覧表示されます。

    2.  フェデレーションサーバーとして構成するコンピューターで、Windows PowerShell コマンドウィンドウを開き、次のコマンドを実行します。

        ```
        Add-AdfsFarmNode -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -PrimaryComputerName <first_federation_server_hostname> -CertificateThumbprint <certificate_thumbprint>
        ```

        `<domain>\<GMSA_name>` は、AD ドメインと、そのドメインの gMSA アカウントの名前です。 `<first_federation_server_hostname>` は、この既存のファーム内のプライマリフェデレーションサーバーのホスト名です。

        の値を取得するには、 `<certificate_thumbprint>` 前の手順でを実行し `dir Cert:\LocalMachine\My` ます。

        > [!NOTE]
        > このコマンドを初めて実行する場合は、パラメーターを追加し `OverwriteConfiguration` ます。

        > [!NOTE]
        > 前のコマンドは、WID ファームノードを作成します。 SQL Server を実行しているコンピューターのサーバーファームノードを作成する場合は、SQL Server のインスタンスが既にインストールされ、動作している必要があります。
        >
        > 次のコマンドを使用して、SQL Server のインスタンスを使用している既存のファームにフェデレーションサーバーを追加できます。ここで、 `Add-AdfsFarmNode -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` **sql \_ ホスト \_ 名** は SQL Server を実行しているサーバーの名前、 **sql \_ インスタンス \_ 名** は SQL Server のインスタンスの名前です。 SQL Server の既定のインスタンスを使用する場合は、 **Sqlconnectionstring** 値として "**データソース \=<SQL \_ ホスト \_ 名>; 統合セキュリティ \= True**" を使用します。

        > [!IMPORTANT]
        > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2008 以降のバージョン (SQL Server 2012 や SQL Server 2014 を含む) を使用できます。

-   既存のドメインユーザーアカウントを使用してフェデレーションサーバーをファームに参加させる場合は、次の手順を実行します。

    1.  フェデレーションサーバーとして構成するコンピューターで、Windows PowerShellcommand ウィンドウを開き、コマンドを実行します `$fscred = get-credential` 。 ドメインユーザー名の形式で、フェデレーションサービスアカウントに使用するドメインユーザーアカウントの資格情報を入力し \\ ます。

    2.  フェデレーションサーバーとして構成するコンピューターで、必要な SSL 証明書が **ローカルコンピューターの \\ My Store** ディレクトリにインポートされていることを確認します。 Windows PowerShellcommand ウィンドウで次のコマンドを実行して、SSL 証明書がインポートされているかどうかを確認 `dir Cert:\LocalMachine\My` できます。 証明書は、 **ローカルコンピューターの \\ My Store** ディレクトリにある拇印によって一覧表示されます。

    3.  同じ Windows PowerShell コマンドウィンドウで、次のコマンドを実行します。

        ```
        Add-AdfsFarmNode -ServiceAccountCredential $fscred -PrimaryComputerName <first_federation_server_hostname> -CertificateThumbprint <certificate_thumbprint>
        ```

        > [!NOTE]
        > このコマンドを初めて実行する場合は、パラメーターを追加し `OverwriteConfiguration` ます。

        > [!NOTE]
        > 前のコマンドは、WID ファームノードを作成します。 SQL Server を実行しているコンピューターのサーバーファームノードを作成する場合は、SQL Server のインスタンスが既にインストールされ、動作している必要があります。 SQL Server のインスタンスを使用して、既存のファームにフェデレーションサーバーを追加するには、次のコマンドを使用します。ここで、 `Add-AdfsFarmNode -ServiceAccountCredential $fscred -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` **sql \_ ホスト \_ 名** は SQL Server のインスタンスが実行されているサーバーの名前、 **sql \_ インスタンス \_ 名** は SQL Server のインスタンスの名前です。 SQL Server の既定のインスタンスを使用する場合は、 **Sqlconnectionstring** 値として "**データソース \=<SQL \_ ホスト \_ 名>; 統合セキュリティ \= True**" を使用します。

        > [!IMPORTANT]
        > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2008 以降のバージョン (SQL Server 2012 や SQL Server 2014 を含む) を使用できます。


\(コンピューターに Active Directory フェデレーションサービス (AD FS) AD FS 役割サービスをインストールすると \) 、このコンピューターをフェデレーションサーバーになるように構成することができます。 次のいずれかの手順を行います。

-   [新しいフェデレーションサーバー ファームでの最初のフェデレーション サーバーの構成](Configure-a-Federation-Server.md#BKMK_1)

-   [フェデレーション サーバーを既存のフェデレーション サーバー ファームに追加する](Configure-a-Federation-Server.md#BKMK_2)

## <a name="configure-the-first-federation-server-in-a-new-federation-server-farm"></a><a name="BKMK_1"></a>新しいフェデレーションサーバー ファームでの最初のフェデレーション サーバーの構成

### <a name="to-configure-the-first-federation-server-in-a-new-federation-server-farm-by-using-the-active-directory-federation-service-configuration-wizard"></a>Active Directory フェデレーションサービス構成ウィザードを使用して、新しいフェデレーションサーバーファームの最初のフェデレーションサーバーを構成するには

> [!NOTE]
> この手順を実行する前に、ドメイン管理者のアクセス許可があること、またはドメイン管理者の資格情報が使用可能であることを確認してください。

1.  Server Manager の [**ダッシュボード**] ページで、[**通知**] フラグをクリックし、[**サーバーにフェデレーション サービスを構成します**] をクリックします。

    **Active Directory フェデレーション サービス構成ウィザード** が開きます。

2.  **[ようこそ]** ページで、**[フェデレーション サーバー ファームに最初のフェデレーション サーバーを作成します]** を選択し、**[次へ]** をクリックします。

3.  [ **AD DS への接続** ] ページで、このコンピューターが参加している Active Directory AD ドメインのドメイン管理者アクセス許可を使用してアカウントを指定 \( し、 \) [ **次へ**] をクリックします。

4.  **[サービスのプロパティの指定]** ページで次の操作を実行してから、**[次へ]** をクリックします。

    -   前の手順で取得した Secure Socket Layer \( SSL \) 証明書とキーを含む .pfx ファイルをインポートします。 [「手順 2: AD FS の SSL 証明書を登録](../../ad-fs/deployment/Enroll-an-SSL-Certificate-for-AD-FS.md)する」では、この証明書を取得し、フェデレーションサーバーとして構成するコンピューターにコピーしました。 ウィザードを使用して .pfx ファイルをインポートするには、[ **インポート**] をクリックし、ファイルの場所を参照します。 メッセージが表示されたら、.pfx ファイルのパスワードを入力します。

    -   フェデレーション サービスの名前を入力します。 たとえば **fs.contoso.com** などです。 この名前は、証明書の件名、またはサブジェクト代替名のいずれかと一致する必要があります。

    -   フェデレーション サービスの表示名を入力します。 たとえば **Contoso Corporation** などです。 ユーザーには、Active Directory フェデレーションサービス (AD FS) AD FS サインインページでこの名前が表示さ \( \) \- れます。

5.  **[サービス アカウントの指定]** ページで、サービス アカウントを指定します。 既存のグループの管理されたサービスアカウント gMSA を作成または使用するか、 \( 既存のドメインユーザーアカウントを使用することができ \) ます。 新しい gMSA アカウントを作成するオプションを選択した場合は、新しいアカウントの名前を指定します。 既存の gMSA アカウントまたはドメインアカウントを使用するオプションを選択した場合は、[ **選択** ] をクリックしてアカウントを選択します。

    > [!NOTE]
    > GMSA アカウントを使用する利点は、自動 \- ネゴシエートパスワード更新機能です。

    > [!WARNING]
    > GMSA アカウントを使用する場合は、Windows Server 2012 オペレーティングシステムを実行している環境内に少なくとも1つのドメインコントローラーが必要です。
    >
    > GMSA オプションが無効になっていて、 **KDS ルートキーが設定されていないためにグループの管理されたサービスアカウントが使用できない** などのエラーメッセージが表示される場合は、Active Directory ドメインで windows Server 2012 以降を実行しているドメインコントローラーで次の windows PowerShell コマンドを実行して、ドメインで gMSA を有効にできます `Add-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)` 。 ウィザードに戻り、[ **前** へ] をクリックし、[ **次へ** ] をクリックして [ \- **サービスアカウントの指定** ] ページに戻ります。 GMSA オプションが有効になります。 これを選択し、使用する gMSA アカウント名を入力できます。

6.  [ **構成データベースの指定** ] ページで、AD FS 構成データベースを指定し、[ **次へ**] をクリックします。 Windows Internal Database WID を使用してこのコンピューターにデータベースを作成するか、 \( \) Microsoft SQL Server の場所とインスタンス名を指定することができます。

    詳細については、「[AD FS 構成データベースの役割](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)」を参照してください。

    > [!IMPORTANT]
    > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2008 以降のバージョン (SQL Server 2012 や SQL Server 2014 を含む) を使用できます。

7.  **[オプションの確認]** ページで、構成の選択内容を確認し、**[次へ]** をクリックします。

8.  [前提 **\- 条件チェック** の実行] ページで、すべての前提条件の確認が正常に完了したことを確認し、[ **構成**] をクリックします。

9. [ **結果** ] ページで結果を確認し、構成が正常に完了したかどうかを確認して、[ **フェデレーションサービスの展開を完了するために必要な次の手順**] をクリックします。 詳細については、「 [AD FS のインストールを完了するための次の手順](https://go.microsoft.com/fwlink/p/?LinkId=286704)」を参照してください。 **[閉じる]** をクリックしてウィザードを終了します。

### <a name="to-configure-the-first-federation-server-in-a-new-federation-server-farm-via-windows-powershell"></a><a name="BKMK_3"></a>Windows PowerShell を使って、新しいフェデレーションサーバー ファームで最初のフェデレーション サーバーを構成するには
新規または既存の gMSA アカウントまたは既存のドメインユーザーアカウントのいずれかを使用して、新しいフェデレーションサーバーファームを作成できます。

-   **新しい gMSA アカウントを使用して新しいフェデレーションサーバーを作成する場合は、次の手順を実行します。**

    > [!IMPORTANT]
    > 新しいフェデレーション サーバー ファームで、最初のフェデレーション サーバーを作成するには、ドメイン管理者権限が必要です。

    1.  フェデレーションサーバーとして構成するコンピューターで、必要な SSL 証明書が **ローカルコンピューターの \\ My Store** ディレクトリにインポートされていることを確認します。 Windows PowerShell コマンドウィンドウで次のコマンドを実行して、SSL 証明書がインポートされているかどうかを確認 `dir Cert:\LocalMachine\My` できます。 証明書は、 **ローカルコンピューターの \\ My Store** ディレクトリにある拇印によって一覧表示されます。

    2.  ドメインコントローラーで、Windows PowerShell コマンドウィンドウを開き、次のコマンドを実行して、KDS ルートキーがドメインに作成されているかどうかを確認します `Get-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)` 。 出力に情報が表示されないように作成されていない場合は、次のコマンドを実行してキーを作成し `Add-KdsRootKey –EffectiveTime (Get-Date).AddHours(-10)` ます。

    3.  フェデレーション サーバーとして構成するコンピューターで、Windows PowerShell コマンド ウィンドウを開き、次のコマンドを実行します。

        ```
        Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -GroupServiceAccountIdentifier <domain>\<GMSA_Name>$
        ```

        > [!WARNING]
        > `$`前のコマンドの最後にある符号が必要です。

        の値を取得するには、 `<certificate_thumbprint>` を実行し、 `dir Cert:\LocalMachine\My` SSL 証明書の拇印を選択します。 `<federation_service_name>` の値はフェデレーション サーバーの名前で、**fs.contoso.com** などです。

        > [!NOTE]
        > このコマンドを初めて実行する場合は、パラメーターを追加し `OverwriteConfiguration` ます。

        > [!NOTE]
        > 前のコマンドは、WID ファームを作成します。 SQL Server サーバーファームを作成する場合は、SQL Server のインスタンスが既にインストールされ、動作している必要があります。
        >
        > 次のコマンドを使用すると、SQL Server のインスタンスを使用する新しいファームに最初のフェデレーションサーバーを作成できます。 `Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -SQLConnectionString "Data Source=<SQL_Host_Name?\<SQL_instance_ name>;Integrated Security=True"` **<sql \_ ホスト \_ 名>** は SQL Server を実行しているサーバーの名前、<**sql \_ インスタンス \_ 名**>は SQL Server のインスタンスの名前です。 SQL Server の既定のインスタンスを使用する場合は、 **Sqlconnectionstring** 値として "**データソース \=<SQL \_ ホスト \_ 名>; 統合セキュリティ \= True**" を使用します。

        > [!IMPORTANT]
        > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2012 など、SQL Server 2008 以降のバージョンを使用できます。

-   **既存のドメインユーザーアカウントを使用して新しいフェデレーションサーバーを作成する場合は、次の手順を実行します。**

    1.  フェデレーションサーバーとして構成するコンピューターで、必要な SSL 証明書が **ローカルコンピューターの \\ My Store** ディレクトリにインポートされていることを確認します。 Windows PowerShell コマンドウィンドウで次のコマンドを実行して、SSL 証明書がインポートされているかどうかを確認 `dir Cert:\LocalMachine\My` できます。 証明書は、 **ローカルコンピューターの \\ My Store** ディレクトリにある拇印によって一覧表示されます。

    2.  フェデレーションサーバーとして構成するコンピューターで、Windows PowerShell コマンドウィンドウを開き、コマンドを実行し `$fscred = Get-Credential` ます。 ドメインユーザー名の形式で、フェデレーションサービスアカウントに使用するドメインユーザーアカウントの資格情報を入力し \\ ます。

    3.  同じ Windows PowerShell コマンド ウィンドウで、次のコマンドを実行します。

        ```
        Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -ServiceAccountCredential $fscred
        ```

        **<証明書の \_ 拇印>** の値を取得するには、 `dir Cert:\LocalMachine\My` を実行し、SSL 証明書の拇印を選択します。 **<フェデレーション \_ サービス \_ 名>** の値は、フェデレーションサービスの名前です。たとえば、fs.contoso.com のようになります。

        > [!NOTE]
        > このコマンドを初めて実行する場合は、パラメーターを追加し `OverwriteConfiguration` ます。

        > [!NOTE]
        > 前のコマンドは、WID ファームを作成します。 SQL Server ファームを作成する場合は、SQL Server のインスタンスが既にインストールされ、動作している必要があります。
        >
        > 次のコマンドを使用して、SQL Server のインスタンスを使用する新しいファームに最初のフェデレーションサーバーを作成できます。ここで、 `Install-AdfsFarm -CertificateThumbprint <certificate_thumbprint> -FederationServiceName <federation_service_name> -ServiceAccountCredential $fscredential -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` **sql \_ ホスト \_ 名** は SQL Server を実行しているサーバーの名前、 **sql \_ インスタンス \_ 名** は SQL Server のインスタンスの名前です。 SQL Server の既定のインスタンスを使用する場合は、 **Sqlconnectionstring** 値として "**データソース \=<SQL \_ ホスト \_ 名>; 統合セキュリティ \= True**" を使用します。

        > [!IMPORTANT]
        > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2008 以降のバージョン (SQL Server 2012 や SQL Server 2014 を含む) を使用できます。

## <a name="add-a-federation-server-to-an-existing-federation-server-farm"></a><a name="BKMK_2"></a>フェデレーション サーバーを既存のフェデレーション サーバー ファームに追加する

> [!IMPORTANT]
> このセクションの手順を開始する前に、「 [手順 3: AD FS の役割サービスをインストール](../../ad-fs/deployment/Install-the-AD-FS-Role-Service.md)する」を完了していることを確認します。

> [!IMPORTANT]
> この手順を実行する前に、有効な SSL サーバー認証証明書を取得していることを確認してください。

### <a name="to-add-a-federation-server-to-an-existing-federation-server-farm-via-the-active-directory-federation-service-configuration-wizard"></a>Active Directory フェデレーション サービス構成ウィザードを使って、フェデレーション サーバーを既存のフェデレーション サーバー ファームに追加するには

1.  Server Manager の [**ダッシュボード**] ページで、[**通知**] フラグをクリックし、[**サーバーにフェデレーション サービスを構成します**] をクリックします。

    **Active Directory フェデレーション サービス構成ウィザード** が開きます。

2.  [ **ようこそ** ] ページで、[フェデレーションサーバー **ファームにフェデレーションサーバーを追加する**] を選択し、[ **次へ**] をクリックします。

3.  [ **AD DS への接続** ] ページで、このコンピューターが参加している AD ドメインのドメイン管理者アクセス許可を使用してアカウントを指定し、[ **次へ**] をクリックします。

4.  [ **ファームの指定** ] ページで、WID を使用するファーム内のプライマリフェデレーションサーバーの名前を指定するか、SQL Server を使用する既存のフェデレーションサーバーファームのデータベースホスト名とデータベースインスタンス名を指定します。

    > [!WARNING]
    > Windows Server &reg; 2012 R2 では、SQL Server の既定のインスタンスを指定するための回避策があります。 この回避策ではユーザー インターフェイスは使用しません。 代わりに、「」の手順に従って、Windows PowerShell を使用して [新しいフェデレーションサーバーファームの最初のフェデレーションサーバーを構成](Configure-a-Federation-Server.md#BKMK_3)します。

    > [!IMPORTANT]
    > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2012 など、SQL Server 2008 以降のバージョンを使用できます。

5.  [ **Ssl 証明書の指定** ] ページで、以前に取得した ssl 証明書とキーを含む .pfx ファイルをインポートします。 この証明書は必須のサービス認証証明書です。 [「手順 2: AD FS の SSL 証明書を登録](../../ad-fs/deployment/Enroll-an-SSL-Certificate-for-AD-FS.md)する」では、この証明書を取得し、フェデレーションサーバーとして構成するコンピューターにコピーしました。 ウィザードを使用して .pfx ファイルをインポートするには、[ **インポート** ] をクリックし、ファイルの場所を参照します。 メッセージが表示されたら、.pfx ファイルのパスワードを入力します。

6.  [ **サービスアカウントの指定** ] ページで、ファームに最初のフェデレーションサーバーを作成したときに構成したものと同じサービスアカウントを指定します。 既存のグループ Managed Service Account や既存のドメイン ユーザー アカウントを使用することもできます。

    > [!IMPORTANT]
    > 指定するアカウントは、このファームのプライマリフェデレーションサーバーで使用されていたアカウントと同じアカウントである必要があります。

7.  **[オプションの確認]** ページで、構成の選択内容を確認し、**[次へ]** をクリックします。

8.  [前提 **\- 条件チェック** の実行] ページで、すべての前提条件の確認が正常に完了したことを確認し、[ **構成**] をクリックします。

9. [ **結果** ] ページで結果を確認し、構成が正常に完了したかどうかを確認して、[ **フェデレーションサービスの展開を完了するために必要な次の手順**] をクリックします。 詳細については、「 [AD FS のインストールを完了するための次の手順](https://go.microsoft.com/fwlink/p/?LinkId=286704)」を参照してください。 **[閉じる]** をクリックしてウィザードを終了します。

### <a name="to-add-a-federation-server-to-an-existing-federation-server-farm-via-windows-powershell"></a>Windows PowerShell を介して、フェデレーション サーバーを既存のフェデレーション サーバー ファームに追加するには
既存の gMSA アカウントまたは既存のドメインユーザーアカウントを使用して、既存のファームにフェデレーションサーバーを追加できます。

-   既存の gMSA アカウントを使用してフェデレーションサーバーをファームに参加させる場合は、次の手順を実行します。

    1.  フェデレーションサーバーとして構成するコンピューターで、必要な SSL 証明書が **ローカルコンピューターの \\ My Store** ディレクトリにインポートされていることを確認します。 Windows PowerShell コマンドウィンドウで次のコマンドを実行して、SSL 証明書がインポートされているかどうかを確認 `dir Cert:\LocalMachine\My` できます。 証明書は、 **ローカルコンピューターの \\ My Store** ディレクトリにある拇印によって一覧表示されます。

    2.  フェデレーションサーバーとして構成するコンピューターで、Windows PowerShell コマンドウィンドウを開き、次のコマンドを実行します。

        ```
        Add-AdfsFarmNode -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -PrimaryComputerName <first_federation_server_hostname> -CertificateThumbprint <certificate_thumbprint>
        ```

        `<domain>\<GMSA_name>` は、AD ドメインと、そのドメインの gMSA アカウントの名前です。 `<first_federation_server_hostname>` は、この既存のファーム内のプライマリフェデレーションサーバーのホスト名です。

        の値を取得するには、 `<certificate_thumbprint>` 前の手順でを実行し `dir Cert:\LocalMachine\My` ます。

        > [!NOTE]
        > このコマンドを初めて実行する場合は、パラメーターを追加し `OverwriteConfiguration` ます。

        > [!NOTE]
        > 前のコマンドは、WID ファームノードを作成します。 SQL Server を実行しているコンピューターのサーバーファームノードを作成する場合は、SQL Server のインスタンスが既にインストールされ、動作している必要があります。
        >
        > 次のコマンドを使用して、SQL Server のインスタンスを使用している既存のファームにフェデレーションサーバーを追加できます。ここで、 `Add-AdfsFarmNode -GroupServiceAccountIdentifier <domain>\<GMSA_name>$ -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` **sql \_ ホスト \_ 名** は SQL Server を実行しているサーバーの名前、 **sql \_ インスタンス \_ 名** は SQL Server のインスタンスの名前です。 SQL Server の既定のインスタンスを使用する場合は、 **Sqlconnectionstring** 値として "**データソース \=<SQL \_ ホスト \_ 名>; 統合セキュリティ \= True**" を使用します。

        > [!IMPORTANT]
        > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2008 以降のバージョン (SQL Server 2012 や SQL Server 2014 を含む) を使用できます。

-   既存のドメインユーザーアカウントを使用してフェデレーションサーバーをファームに参加させる場合は、次の手順を実行します。

    1.  フェデレーションサーバーとして構成するコンピューターで、Windows PowerShellcommand ウィンドウを開き、コマンドを実行します `$fscred = get-credential` 。 ドメインユーザー名の形式で、フェデレーションサービスアカウントに使用するドメインユーザーアカウントの資格情報を入力し \\ ます。

    2.  フェデレーションサーバーとして構成するコンピューターで、必要な SSL 証明書が **ローカルコンピューターの \\ My Store** ディレクトリにインポートされていることを確認します。 Windows PowerShellcommand ウィンドウで次のコマンドを実行して、SSL 証明書がインポートされているかどうかを確認 `dir Cert:\LocalMachine\My` できます。 証明書は、 **ローカルコンピューターの \\ My Store** ディレクトリにある拇印によって一覧表示されます。

    3.  同じ Windows PowerShell コマンドウィンドウで、次のコマンドを実行します。

        ```
        Add-AdfsFarmNode -ServiceAccountCredential $fscred -PrimaryComputerName <first_federation_server_hostname> -CertificateThumbprint <certificate_thumbprint>
        ```

        > [!NOTE]
        > このコマンドを初めて実行する場合は、パラメーターを追加し `OverwriteConfiguration` ます。

        > [!NOTE]
        > 前のコマンドは、WID ファームノードを作成します。 SQL Server を実行しているコンピューターのサーバーファームノードを作成する場合は、SQL Server のインスタンスが既にインストールされ、動作している必要があります。 SQL Server のインスタンスを使用して、既存のファームにフェデレーションサーバーを追加するには、次のコマンドを使用します。ここで、 `Add-AdfsFarmNode -ServiceAccountCredential $fscred -SQLConnectionString "Data Source=<SQL_Host_Name>\<SQL_instance_ name>;Integrated Security=True"` **sql \_ ホスト \_ 名** は SQL Server のインスタンスが実行されているサーバーの名前、 **sql \_ インスタンス \_ 名** は SQL Server のインスタンスの名前です。 SQL Server の既定のインスタンスを使用する場合は、 **Sqlconnectionstring** 値として "**データソース \=<SQL \_ ホスト \_ 名>; 統合セキュリティ \= True**" を使用します。

        > [!IMPORTANT]
        > AD FS ファームを作成し、SQL Server を使用して構成データを保存する場合は、SQL Server 2008 以降のバージョン (SQL Server 2012 や SQL Server 2014 を含む) を使用できます。

## <a name="see-also"></a>関連項目

[AD FS 展開](../../ad-fs/AD-FS-Deployment.md)

[Windows Server 2012 R2 AD FS の展開ガイド](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)

[フェデレーション サーバー ファームの展開](../../ad-fs/deployment/Deploying-a-Federation-Server-Farm.md)



