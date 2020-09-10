---
title: Windows Server Essentials での Microsoft 365 の管理
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 3f8485e4-e10f-4f38-8a5e-d5227abd0d84
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 71e8204c8b11f423871f890badffdfb96206feb8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623060"
---
# <a name="manage-microsoft-365-in-windows-server-essentials"></a>Windows Server Essentials での Microsoft 365 の管理

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

Windows Server Essentials サーバーと Microsoft 365 を統合すると、Windows Server Essentials ダッシュボードから、Microsoft 365 サービスとオンラインアカウントをオンプレミスのリソースと共に管理できます。 このトピックでは、サーバーと Microsoft 365 を統合することによって得られるメリット、その方法、Microsoft 365 統合の管理およびトラブルシューティングを行う方法について説明します。



> [!IMPORTANT]
>   Microsoft 365 統合は、単一ドメインコントローラー環境でのみサポートされます。 また、Microsoft 365 統合ウィザードは、ドメインコントローラー上で実行する必要があります。

## <a name="in-this-topic"></a>このトピックの内容

-   [Microsoft 365 をサーバーと統合する必要があるのはなぜですか。](#BKMK_IntegrationOverview)

-   [Microsoft 365 統合のセットアップ](Manage-Office-365-in-Windows-Server-Essentials.md#BKMK_Configure)

-   [Microsoft 365 統合の管理](#BKMK_ManageIntegration)

-   [Microsoft 365 統合のトラブルシューティング](Manage-Office-365-in-Windows-Server-Essentials.md#BKMK_Troubleshoot)

##  <a name="why-should-i-integrate-microsoft-365-with-my-server"></a><a name="BKMK_IntegrationOverview"></a> Microsoft 365 をサーバーと統合する必要があるのはなぜですか。
 Microsoft 365 を Windows Server Essentials サーバーと統合するには、さまざまな理由があります。 社内のリソースの一部を管理していても、他のサービスに Microsoft 365 を使用している場合は、2か所で作業するのではなく、ダッシュボードからオンプレミスのリソースと共に Microsoft 365 サービスとリソースを管理できるようになります。

- ユーザーアカウントと共に Microsoft 365 へのアクセス権をユーザーに与えるオンラインアカウントを管理します。

  -   ユーザー用の Microsoft Online Services アカウントを 1 つの手順で作成し、既存のオンライン アカウント用にサーバー上にユーザー アカウントを作成します。 新規または既存のユーザー アカウントにオンライン アカウントを追加することもできます。

       ダッシュボードからオンラインアカウントを作成すると、ユーザーは、サーバーで使用しているのと同じパスワードを使用して Microsoft 365 にサインインします。 ユーザーがユーザー アカウントのパスワードを変更した場合は、オンラインのパスワードも変わります。 ユーザー アカウントに対して設定したセキュリティ要件をオンライン アカウントのパスワードが常に満たしていることがわかります。

  -   ユーザー アカウントのライフ サイクルを通して、ユーザー アカウントと共にオンライン アカウントを管理します。 ユーザー アカウントを無効にすると、オンライン アカウントも無効になります。 ユーザー アカウントを削除すると、オンライン アカウントも削除されます。

  -   Windows Server Essentials サーバーでは、電子メールの Exchange Online 配布グループも管理します。

- カスタムインターネットドメインを Microsoft 365 サブスクリプションにリンクして、組織のインターネットドメイン (たとえば、contoso.com) から電子メールを送受信します。

- ダッシュボードからサブスクリプションと Microsoft 365 統合を管理します。

- サブスクリプションに SharePoint Online ライブラリが含まれている場合、Microsoft 365 と Windows Server Essentials サーバーを統合すると、次のことができます。

  - ダッシュボードから SharePoint Online ライブラリを作成し、管理します。

    > [!NOTE]
    >  また、My Server 2012 R2 アプリを使用して、ノート pc、モバイルデバイス、または Windows phone から SharePoint Online ライブラリ内のドキュメントを操作することもできます。 この機能は、Windows Server Essentials でのみ使用できます。 詳細については、「 [My Server アプリを使用する](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)」を参照してください。

  - ダッシュボードから SharePoint Online チームサイトのアクセス許可を変更するか、ダッシュボードからチームサイトを開いて他の変更を行います。

    詳細については、「 [SharePoint Online の管理](Manage-SharePoint-Online-in-Windows-Server-Essentials.md)」を参照してください。

- Exchange Online にサブスクライブしている場合は、Microsoft 365 Windows Server Essentials サーバーとの統合により、ユーザーが会社の電子メールサーバーへの接続に使用するモバイルデバイスを管理できます。

  -   モバイル デバイスが会社の電子メール サーバーに接続するときにパスワード保護を必要とします。 最小のパスワード長、サインインの許容失敗回数、およびサインイン試行の必須最小時間間隔を設定します。

  -   デバイス モデルにセキュリティ上の問題があることがわかったら、Exchange Online へのそのモバイル デバイスの接続をブロックします。

  -   モバイル デバイスの紛失または盗難発生の場合は、デバイスの電源が次にオンにされたときに、企業の機密データを削除するようにデバイスをワイプします。

- Microsoft 365 統合を使用すると、Microsoft 365 サービスとリソースに接続するための新しい方法が提供されます。

  -   Windows Server Essentials スタートパッドから Microsoft 365 services を開きます。 詳細については、「 [Microsoft 365 を使用](../use/Quick-Start-Guide-to-Using-Microsoft-Office-365-with-Windows-Server-Essentials.md)したクイックスタートガイド」を参照してください。

  -   My Server 2012 R2 アプリを使用して、ノート pc、モバイルデバイス、または Windows phone から SharePoint Online ライブラリ内のドキュメントを操作します。 詳細については、「 [My Server アプリを使用する](../use/Use-the-My-Server-App-to-Connect-to-Windows-Server-Essentials.md)」を参照してください。 この機能は、Windows Server Essentials でのみ使用できます。

##  <a name="set-up-microsoft-365-integration"></a><a name="BKMK_Configure"></a> Microsoft 365 統合のセットアップ
 サーバーのインストールが完了したら、いつでもサーバーを Microsoft 365 と統合できます。 まだ Microsoft 365 サブスクリプションをお持ちでない場合は、購入するか、無料試用版サブスクリプションにサインアップすることができます。

 次のタスクを行います。

-   [手順 1: Microsoft 365 統合要件を確認する](#BKMK_StepOne_VERIFY)

-   [手順 2: サーバーを Microsoft 365 と統合する](#BKMK_StepTwo)

-   [手順 3: 組織のインターネットドメイン名を Microsoft 365 にリンクする (省略可能)](#BKMK_StepThree)

###  <a name="step-1-verify-microsoft-365-integration-requirements"></a><a name="BKMK_StepOne_VERIFY"></a> 手順 1: Microsoft 365 統合要件を確認する
 開始する前に、サーバーが次の要件を満たしてされていることを確認します。

-   サーバーには、windows server essentials、Windows Server Essentials、windows server 2012 R2 Standard、windows server 2012 R2 Datacenter オペレーティングシステム (Windows server Essentials Experience 役割がインストールされている) のいずれかのオペレーティングシステムが搭載されています。

-   環境で使用できるドメインコントローラーは1つだけであるため、ドメインコントローラー上で Microsoft 365 統合を実行する必要があります。

-   サーバーからインターネットに接続できる必要があります。

-   Microsoft 365 統合を開始する前に、すべての重要な更新プログラムと重要な更新プログラムをサーバーにインストールする必要があります。

-   組織のインターネットドメインを電子メールアドレスと SharePoint Online リソースで使用する場合は、統合時にドメインを Microsoft 365 にリンクできるようにドメイン名を登録する必要があります。 詳細については、「 [ドメイン名の購入方法](https://office.microsoft.com/office365-suite-help/how-to-buy-a-domain-name-HA102819883.aspx?CTT=5&origin=HA102818660)」を参照してください。

> [!NOTE]
>  事前に Microsoft 365 をサブスクライブする必要はありません。 Microsoft 365 統合中にサブスクリプションを購入するか、無料試用版にサインアップすることができます。 Microsoft 365 のプランと価格を確認する場合は、 [Microsoft 365 プランと企業を比較](https://office.microsoft.com/compare-office-365-for-business-plans-FX102918419.aspx?CR_CC=200061904&WT.srch=1&WT.mc_ID=PS_bing_O365Comm_subscribe-to-office-365_Text)してください。

###  <a name="step-2-integrate-the-server-with-microsoft-365"></a><a name="BKMK_StepTwo"></a> 手順 2: サーバーを Microsoft 365 と統合する
 Windows Server Essentials サーバーと Microsoft 365 を統合するには、ドメインコントローラーで次の手順を実行します。

> [!NOTE]
>  この手順は、Windows Server Essentials または Windows Server Essentials を使用している場合と同じですが、ホームページの別の場所から開始します。 Windows Server Essentials では、[ **サービス** ] タブでサーバーを Microsoft 365 およびその他の Microsoft オンラインサービスと統合します。Windows Server Essentials では、[ **電子メール** ] タブで Microsoft 365 統合が実行されます。

##### <a name="to-integrate-the-server-with-microsoft-365"></a>サーバーを Microsoft 365 と統合するには

1. 管理者としてサーバーにサインインし、Windows Server Essentials ダッシュボードを開きます。

2. [ **ホーム** ] ページで、[ **サービス** ] (Windows Server Essentials の場合は [ **電子メール**]) をクリックし、[ **Microsoft 365 との統合**] をクリックして、[ **Microsoft 365 統合のセットアップ**] をクリックします。

    Microsoft 365 の統合ウィザードが表示されます。

3. [**はじめよう**] ページで、次の操作のいずれかを実行します。

   -   Microsoft 365 するサブスクリプションがない場合は、[ **次へ**] をクリックし、指示に従って Microsoft 365 に登録するか、試用版サブスクリプションにサインアップしてください。

        ウィザードに戻る前に、Microsoft 365 にサインインする必要があります。 ただし、Microsoft 365 ポータルの [ **ここから開始** ] セクションでタスクを実行する必要はありません。

   -   サーバーと統合する Microsoft 365 のサブスクリプションを既に持っている場合は、[ **Microsoft 365 のサブスクリプションが既にある**] を選択し、[ **次へ**] をクリックします。

4. 指示に従ってウィザードを完了します。

   ウィザードが正常に完了すると、ダッシュボードに次のような変更が加えられます。

-   新しい **Microsoft 365** ページがあります。これは、統合と Microsoft 365 サブスクリプションを管理するために使用されます。

-   [ **ユーザー** ] ページに [ **オンラインアカウント** ] タブが表示されます。このタブでは、ユーザーが Microsoft 365 にアクセスできるようにする Microsoft online Services アカウントを作成および管理できます。 Exchange Online を使用していて、Windows Server Essentials サーバーを持っている場合は、[ **配布グループ** ] タブも表示されます。

-   Windows Server Essentials サーバーの [ **ストレージ** ] ページには、sharepoint Online ライブラリを管理したり、チームサイトのアクセス許可を変更したりするための [ **sharepoint ライブラリ** ] タブがあります。 Microsoft 365 のすべてのビジネスプランには、これらの基本的な SharePoint Online 機能が含まれています。

###  <a name="step-3-link-your-organizations-internet-domain-name-to-microsoft-365-optional"></a><a name="BKMK_StepThree"></a> 手順 3: 組織のインターネットドメイン名を Microsoft 365 にリンクする (省略可能)
 組織宛ての電子メールと SharePoint Online リソースの Url で独自のインターネットドメインを使用する場合は、カスタムドメインを Microsoft 365 サブスクリプションにリンクできます。 Windows Server Essentials サーバーを Microsoft 365 と統合する場合は、ダッシュボードからこの操作を行うことができます。

 これは、オンラインアカウントを一括作成するときにドメインを使用できるように、ユーザーのオンラインアカウントを作成する前に実行するのが最も簡単です。

 Microsoft 365 にサインアップすると、ドメイン名が取得されます。たとえば、 *contoso*. onmicrosoft.com のようになります。 別のドメイン名を使用する場合は、簡単に contoso.com ことができます。 ドメイン名をまだ所有していない場合は購入し、DNS レコードの一部を変更する必要があります。

 Microsoft 365 で使用するカスタムドメインのセットアップには、次の4つのタスクが含まれます。

1. **ドメイン名を購入します。** つまり、ドメイン名をドメイン レジストラーまたは DNS ホスティング プロバイダーに登録します。

   -   Microsoft 365 で動作するドメイン名を選択します。 第2レベルのドメイン名を使用できますか。たとえば、buycontoso.com? ではなく、3番目のレベルのドメイン名は使用できません。たとえば、marketing.contoso.com のように指定します。 Microsoft 365 で使用するドメインの選択の詳細については、「 [ドメイン](/office365/servicedescriptions/office-365-platform-service-description/domains)」を参照してください。

   -   Microsoft 365 に必要なドメインネームサーバー (DNS) レコードを許可するドメインレジストラーから購入します。 どのドメイン レジストラーが、必要な DNS レコードを許可しているかを調べるには、「 [ドメイン名の購入方法](https://office.microsoft.com/office365-suite-help/how-to-buy-a-domain-name-HA102819883.aspx?CTT=5&origin=HA102818660)」を参照してください。 ドメインを別のレジストラーに既に登録している場合は、心配しないでください。ドメインを Microsoft 365 にリンクするときに、ドメインを別のレジストラーに転送できます。

2. **Microsoft 365 サービスがドメイン名を使用できるようにする DNS レコードを構成します。** 最も簡単な方法は、手順 3. でドメインを Microsoft 365 サブスクリプションにリンクするときに、ウィザードで DNS レコードを構成することです。 自分で実行する場合は、「 [Microsoft 365 統合のために DNS レコードを手動で構成する方法](#BKMK_ManuallyConfigureDNS)」を参照してください。

3. **カスタムインターネットドメインを Microsoft 365 サブスクリプションにリンクします。** Microsoft 365 アクションへの **ドメインのリンクを** 使用します。

4. **Microsoft 365 サービスが新しいドメイン名を使用していることを確認します。**

   [ **ドメインを Microsoft 365 にリンクする** ] タスクを使用する前に手順 1. と手順 2. を完了すると、ウィザードによってドメイン名を Microsoft 365 にリンクできます。 あるいは、手順 1 および手順 2 の一部または全部をウィザードを使用して実行することもできます。

##### <a name="to-link-your-organizations-internet-domain-to-microsoft-365"></a>組織のインターネットドメインを Microsoft 365 にリンクするには

1.  ダッシュボードで、[ **Microsoft 365** ] ページを開き、[ **ドメインを Microsoft 365 にリンク**します] をクリックします。

2.  指示に従ってウィザードを完了します。

     このウィザードでは、Microsoft 365 で使用する新規または既存のインターネットドメイン名を登録、構成、およびリンクする手順の一部またはすべてを行うことができます。

     タスクを完了するために必要な情報を取得するには、ウィザード ページで [ヘルプ] リンクをクリックします。 または、プロセスの概要と要件については、「 [Windows Server Essentials でのリモート Web アクセスの管理](https://technet.microsoft.com/library/jj628152\(d=printer\).aspx) 」の「ドメイン名のセットアップ」セクションを参照してください。

    > [!NOTE]
    >  ウィザードを使用して新しいドメイン名を登録するには、ウィザードとのシームレスな統合を提供するために Microsoft と提携しているドメイン名サービス プロバイダーのいずれかを使用する必要があります。 ドメイン名レジストラ－を見つけるには、「 [ドメイン名の購入方法](https://office.microsoft.com/office365-suite-help/how-to-buy-a-domain-name-HA102819883.aspx?CTT=5&origin=HA102818660)」を参照してください。

3.  ドメイン名がサーバーで管理されていないことがウィザードによって検出された場合は、構成を完了するために必要な DNS レコードを手動で構成する必要があります。 手順については、このトピックの「 [Microsoft 365 の統合のために DNS レコードを手動で構成する方法](#BKMK_ManuallyConfigureDNS)」を参照してください。

4.  ドメインが Microsoft 365 で使用されていることを確認します。

     ウィザードが完了した後、ドメイン名レジストラーによって DNS レコードが検証されるまで、少し待機します。 これは自動的に行われます。何もする必要はありません。 しかし、通常は1時間ほどかかります。 ドメインの検証が完了すると、[ **Microsoft 365** ] ページに組織のドメインが一覧表示されます。

####  <a name="how-to-manually-configure-dns-records-for-microsoft-365-integration"></a><a name="BKMK_ManuallyConfigureDNS"></a> Microsoft 365 統合のために DNS レコードを手動で構成する方法
 ドメイン名がサーバーによって管理されていないことが検出された場合は、ドメインへのリンクの Microsoft 365 ウィザードで、必要なドメインネームサーバー (DNS) レコードを手動で構成する必要があります。 この場合、 **% username% \ NewDNSRecords_ (n) .txt**で構成する必要がある DNS レコードの一覧があります。 *(n)* はランダムな数値です。

 次の表は、追加する必要がある DNS レコードを説明します。 入力方法は、ドメイン名レジストラーによって異なります。 不明な点がある場合は、ドメイン名のレジストラーにお問い合わせください。

### <a name="required-dns-records-for-linking-a-custom-internet-domain-name-to-microsoft-365"></a>カスタムインターネットドメイン名を Microsoft 365 にリンクするために必要な DNS レコード

|サービス|必要な DNS レコード|目的|
|-------------|--------------------------|-------------|
|(複数のサービス)|MX| Microsoft 365 は、このレコードを使用して、特定のドメイン名を所有していることを確認します。 この MX レコードは、電子メール メッセージのルーティングには影響しません。|
|Exchange Online|MX|電子メール メッセージのルーティングを実現します。 **重要:**  電子メールを移行する場合は、新しい MX レコードにゼロ (**0**) の設定を割り当てないでください。 レコードの値が現在の MX レコードに割り当てられている値より大きいことを確認してください。 電子メールの移行が完了し、電子メールサーバーを Microsoft 365 に変更する準備ができたら、ドメイン名レジストラーに新しい MX レコードの優先順位の値をリセットさせます。|
|Exchange Online|エイリアス (CNAME)|ユーザーが Exchange Online と Outlook デスクトップ クライアントまたはモバイル電子メール クライアントとの接続を容易にセットアップできるように支援するための自動検出レコード。 **注:**  組織独自のドメイン名を使用して Outlook Web アクセスにアクセスする場合は (たとえば、 http://mail.contoso.com) 標準の URL () の代わりに、 https://outlook.com/owa/office365.com) エイリアス (cname) レコードを次のように構成できます。 **Type = cname、TTL = 01:00:00、HostName = mail、Address = mail. office365 .com**|
|Exchange Online|TXT|Microsoft 365 電子メールサーバーによって使用されるドメイン outlook.com が、ドメインの代わりに電子メールを送信する権限を持つことを指定します。 このレコードを作成すれば、送信電子メールがスパムとしてフラグ付けされるのを容易に防ぐことができます。|
|Lync Online|SRV|Windows Live や Yahoo! などのその他のインスタント メッセージング サービスでフェデレーションを有効にするのに役立ちます。|
|Lync Online|SRV|ユーザーが Lync デスクトップ クライアントと Microsoft Lync Online の間の接続を簡単にセットアップできるように支援するための自動検出レコード。|

> [!IMPORTANT]
>  ドメインの検証が完了したら、Microsoft 365 ポータルから DNS レコードを追加したり、変更を加えたりしないでください。

###  <a name="next-step"></a><a name="BKMK_StepFour_ACCOUNTS"></a> 次のステップ

-   ユーザー用の Microsoft Online Services アカウントを作成します。

     Microsoft 365 サービスを使用するには、ユーザーは、ネットワークユーザーアカウントに関連付けられている Microsoft Online Services アカウントを持っている必要があります。 ダッシュボードは、これを容易にします。 新しい Microsoft 365 サブスクリプションを使用している場合は、既存のユーザーアカウントのオンラインアカウントを一括作成できます。 既に使用している Microsoft 365 サブスクリプションと新しいサーバーを統合する場合は、既存のオンラインアカウントからユーザーアカウントをインポートできます。 手順については、「 [ユーザーのオンラインアカウントを管理する](Manage-Online-Accounts-for-Users.md)」を参照してください。

> [!NOTE]
>  Windows Server Essentials のダッシュボードでは、Microsoft Online Services アカウントは Microsoft 365 アカウントと呼ばれます。 アカウントは同じで、用語だけが変更されています。

##  <a name="manage-microsoft-365-integration"></a><a name="BKMK_ManageIntegration"></a> Microsoft 365 統合の管理
 サーバーを Microsoft 365 と統合すると、ダッシュボードの [ **Microsoft 365** ] ページに Microsoft 365 サブスクリプションに関する情報が表示され、これらのタスクが使用できるようになります。

-   [Microsoft 365 サブスクリプションを管理し](#BKMK_ManageO365) ますか?サブスクリプションの管理に使用する管理者アカウントを変更します。 Microsoft 365 管理ダッシュボードを開いて、サブスクリプションを管理します。

-   [組織のインターネットドメインを Microsoft 365 にリンクし](#BKMK_StepThree) ますか?独自のドメイン宛ての電子メールを送受信できるようにするには、ドメインを Microsoft 365 にリンクします。 (前述の [手順 3: 組織のドメインを Microsoft 365 にリンク](#BKMK_StepThree)します)。

-   [Microsoft 365 統合を無効に](#BKMK_Disable) しますか?Microsoft 365 サービス、サブスクリプション、およびオンラインアカウントをダッシュボードから管理しない場合は、Microsoft 365 統合を無効にすることができます。 サービスは Microsoft 365 ポータルで引き続き利用できます。

###  <a name="manage-your-microsoft-365-subscription"></a><a name="BKMK_ManageO365"></a> Microsoft 365 サブスクリプションの管理
 サーバーでの作業中に Microsoft 365 サブスクリプションに変更を加える必要がある場合は、ダッシュボードの [ **Microsoft 365** ] ページから Microsoft 365 でサブスクリプションを開くことができます。 また、サーバーが Microsoft 365 サービスに変更を加えるときに使用する管理者アカウントを変更することもできます。

##### <a name="to-open-your-subscription-on-the-microsoft-365-admin-dashboard"></a>Microsoft 365 管理ダッシュボードでサブスクリプションを開くには

1.  Windows Server Essentials ダッシュボードで、[ **Microsoft 365** ] ページを開きます。

2.  [ **構成タスク**] で、[ **Microsoft 365 の管理**] をクリックします。

3.  サブスクリプションの管理に使用する Microsoft オンラインアカウントを使用して Microsoft 365 にサインインします。

     Microsoft 365 管理ダッシュボードが開きます。

##### <a name="to-change-the-microsoft-365-administrator-account"></a>Microsoft 365 管理者アカウントを変更するには

1.  ダッシュボードで、[ **Microsoft 365**] をクリックします。

2.  [ **構成タスク**] で、[ **Microsoft 365 管理者アカウントの変更**] をクリックします。 管理者アカウントの変更ウィザードが表示されます (Windows Server Essentials では、ウィザードの名前は Microsoft 365 管理者アカウントに設定されています)。

3.  Microsoft 365 サブスクリプションへの接続に使用するアカウントの資格情報を入力し、[ **次へ**] をクリックします。

4.  **[閉じる]** をクリックします。 ダッシュボードが再起動します。

###  <a name="disable-microsoft-365-integration"></a><a name="BKMK_Disable"></a> Microsoft 365 統合を無効にする
 Microsoft 365 services とオンラインアカウントをダッシュボードから管理しない場合は、Microsoft 365 統合を無効にすることができます。 Microsoft 365 サブスクリプションはアクティブなままで、ダッシュボードから行った構成の変更は引き続き有効になります。 たとえば、Microsoft 365 サブスクリプションにリンクしたドメイン名宛ての電子メールを受信します。 すべての電子メールが失われることはなく、モバイルデバイス用に設定したコントロールは引き続き Exchange Online で使用されます。

 今後は、Microsoft 365 で Microsoft 365 サブスクリプション、サービス、リソースを管理することになり、ユーザーは Microsoft 365 でオンラインアカウントのパスワードを管理する必要があります。 パスワード同期は行われなくなり、ユーザーアカウントを無効にしたり削除したりしても、ユーザーのオンラインアカウントに影響はありません。

 Microsoft 365 統合ソフトウェアがローカルサーバーにインストールされているため、統合サービスが Microsoft 365 に接続できない場合でも、この機能を無効にすることができます。

##### <a name="to-disable-microsoft-365-integration-with-the-server"></a>サーバーとの Microsoft 365 の統合を無効にするには

1.  ダッシュボードで、[ **Microsoft 365**] をクリックします。

2.  [ **Microsoft 365 統合を無効にする] を**クリックします。 Microsoft 365 の無効化ウィザードが表示されます。

3.  指示に従ってウィザードを完了します。

> [!NOTE]
>  Microsoft 365 統合を再び有効にするには、ダッシュボードの**ホーム**ページの [**サービス**] タブにある [ **Microsoft 365 との統合**] タスクを使用します。 手順については、このトピックで前述し [た「手順 2: Windows Server Essentials サーバーを Microsoft 365 に統合する](#BKMK_StepTwo)」を参照してください。

##  <a name="troubleshoot-microsoft-365-integration"></a><a name="BKMK_Troubleshoot"></a> Microsoft 365 統合のトラブルシューティング
 このセクションでは、Windows Server Essentials の Microsoft 365 統合機能を使用するときに発生する可能性のある一般的な問題のトラブルシューティングに役立つ情報を提供します。

###  <a name="some-microsoft-online-services-accounts-were-not-created"></a><a name="BKMK_AcctsNotCreated"></a> 一部の Microsoft Online Services アカウントが作成されませんでした
 **説明**

 ダッシュボードから1つ以上の Microsoft Online Services アカウントを作成できませんでした。

 **解決方法**

1.  ウィザードの完了ページにあるリンクをクリックして、正常終了しなかった各アカウント作成要求に関する詳細な情報が含まれる結果ファイルを開きます。 たとえば、要求したアカウント名を持つ Microsoft Online Services アカウントが既に存在するという結果が示される場合があります。

2.  推奨される操作に従って、各エラーを解決します。

3.  この問題が解決しない場合は、サーバーを再起動して、オンライン アカウントの作成を再度試みます。

###  <a name="there-was-a-problem-uninstalling-microsoft-365-integration"></a><a name="BKMK_ProblemUninstalling"></a> Microsoft 365 統合のアンインストールで問題が発生しました
 **説明**

 Microsoft 365 統合を無効にしようとしたときに不明なエラーが発生しました。

 **解決方法**

1.  コンピューターがインターネットに接続されていることを確認してから、再試行してください。

2.  エラーが再び発生する場合は、サーバーを再起動し、もう一度試してください。

## <a name="additional-references"></a>その他の参照情報

-   [Windows Server Essentials のサービス統合の概要-パート1](/archive/blogs/sbs/services-integration-overview-for-windows-server-2012-r2-essentials-part-1)

-   [Windows Server Essentials のサービス統合の概要-パート2](/archive/blogs/sbs/services-integration-overview-for-windows-server-2012-r2-essentials-part-2)

-   [Microsoft 365 を使用するクイックスタートガイド](../use/Quick-Start-Guide-to-Using-Microsoft-Office-365-with-Windows-Server-Essentials.md)

-   [Microsoft Online Services の管理](../manage/Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)

-   [Windows Server Essentials の管理](../manage/Manage-Windows-Server-Essentials.md)