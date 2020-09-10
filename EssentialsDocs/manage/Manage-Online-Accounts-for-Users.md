---
title: Windows Server Essentials ユーザーのオンライン アカウントの管理
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: c09f4cf6-4d12-49fe-9ae4-e6cb14027b9d
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 3506f83ae2d6b5fc3d49376193cbf3c59e36fb65
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89623048"
---
# <a name="manage-online-accounts-for-windows-server-essentials-users"></a>Windows Server Essentials ユーザーのオンライン アカウントの管理

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

Windows Server Essentials サーバーと Microsoft 365 を統合すると、ダッシュボードからユーザーアカウントと共にオンラインアカウントを管理できます。 このトピックでは、ダッシュボードからユーザーの Microsoft Online Services アカウントを管理することで得られるメリット、ダッシュボードからオンラインアカウントを作成および管理する方法、ダッシュボードから Exchange Online の電子メールアドレスと配布グループを管理する方法について説明します。


> [!NOTE]
>  Windows Server Essentials で Microsoft Online Services アカウントを管理するには、サーバーを Microsoft 365 と統合する必要があります。 手順については、「 [Manage Microsoft 365](Manage-Office-365-in-Windows-Server-Essentials.md)」を参照してください。

> [!IMPORTANT]
>  Windows Server Essentials でオンラインアカウントを管理している場合は、 *Microsoft 365 アカウント*と呼ばれる Microsoft online Services アカウントが表示されます。 Windows Server Essentials のダッシュボードでは、ラベルが *Microsoft Online Services アカウント*、または短い *microsoft オンラインアカウント* に変更されました。 アカウントと手順は同じです。ラベルだけが変更されています。 このトピックのほとんどの手順では、用語*オンライン アカウント*を使用します。

## <a name="in-this-topic"></a>このトピックの内容

-   [ダッシュボードからオンライン アカウントを管理する理由](#BKMK_WhyManageOnlineAccounts)

-   [オンライン アカウントの作成](#BKMK_SECTION_CreateOnlineAccounts)

-   [オンライン アカウントの管理](#BKMK_SECTION_ManageOnlineAccounts)

-   [Exchange Online の電子メール アドレスの管理](#BKMK_SECTION_ManageEmailAddresses)

-   [Exchange Online の配布グループの管理](#BKMK_SECTION_ManageDistributionGroups)

##  <a name="why-should-i-manage-my-online-accounts-from-the-dashboard"></a><a name="BKMK_WhyManageOnlineAccounts"></a> ダッシュボードからオンラインアカウントを管理する必要があるのはなぜですか。
 ダッシュボードを使用して Microsoft Online Services アカウントをユーザーアカウントに割り当てると、アカウントのパスワードが自動的に同期され、ユーザーアカウントのライフサイクル全体で2つのアカウントを一緒に維持することができます。

 ユーザーにとっては便利です。同じパスワードを使用して、サーバー上のリソースや Microsoft 365 にアクセスできます。 また、社内のリソースに必要な Microsoft 365 のリソースにアクセスする場合も、同じパスワード要件を適用できます。

### <a name="how-does-password-synchronization-work"></a>パスワード同期化のしくみ
 ダッシュボードを使用して Microsoft Online Services アカウントをユーザーアカウントに割り当てると、ユーザーアカウントのパスワードが自動的にユーザーのオンラインアカウントと同期されます。 つまり、ユーザーは、サーバー上のリソースと Microsoft 365 の両方のリソースにアクセスするために1つのパスワードしか必要としません。 さらに、ユーザーアカウントとユーザーのオンライン ID に同じ名前を使用できます。

 パスワードの同期は、ドメインに参加しているコンピューターまたはリモート Web アクセスを使用してユーザー アカウントのパスワードを変更した直後に自動で行われます。

> [!IMPORTANT]
>  Microsoft 365 が Windows Server Essentials と統合されている場合、ユーザーは Microsoft 365 ポータルから Microsoft オンラインアカウントのパスワードを変更しないでください。 それを行うと、パスワードの同期化は中断されます。

### <a name="simplified-account-creation"></a>簡素化されたアカウントの作成
 ダッシュボードから最初のオンラインアカウントを作成すると、もう1つの利点があります。 単一の操作で、すべてのユーザーのオンライン アカウントを作成できます。 一方、従業員が既に Microsoft 365 を使用していて、新しい Windows Server Essentials サーバーを設定している場合は、1回の操作でオンラインアカウントからすべてのユーザーアカウントを作成できます。 詳細については、「[オンライン アカウントの作成](#BKMK_SECTION_CreateOnlineAccounts)」を参照してください。

### <a name="manage-email-addresses-and-distribution-groups-from-the-dashboard"></a>ダッシュボードから電子メール アドレスと配布グループを管理する
 Exchange Online の電子メール アドレスと配布グループは、ダッシュボードから管理することができます。 また、電子メールアドレスで組織のインターネットドメインを使用することもできます。 この操作はすべて、Microsoft 365 にサインインしなくても、ダッシュボードから行うことができます。 (ダッシュボードから配布グループを管理するには、Windows Server Essentials を使用する必要があります。 この機能は、Windows Server Essentials ではサポートされていません。)詳細については、「 [Exchange online の電子メールアドレスを管理](#BKMK_SECTION_ManageEmailAddresses) する」と「 [exchange online の配布グループを管理](#BKMK_SECTION_ManageDistributionGroups)する」を参照してください。

### <a name="manage-the-user-account-and-online-account-together"></a>ユーザー アカウントとオンライン アカウントを一緒に管理する
 また、アカウントのライフサイクル全体で、ユーザーアカウントと共にオンラインアカウントを管理できます。 ユーザー アカウントを非アクティブにすると、Microsoft Online Services でオンライン アカウントも非アクティブにされます。 ユーザー アカウントを削除すると、オンライン アカウントも削除されます。 詳細については、「[オンライン アカウントを管理する](#BKMK_SECTION_ManageOnlineAccounts)」を参照してください。

##  <a name="create-online-accounts"></a><a name="BKMK_SECTION_CreateOnlineAccounts"></a> オンラインアカウントを作成する
 サーバーを Microsoft 365 と統合すると、ダッシュボードからユーザー用の Microsoft Online Services アカウントを作成できるようになります。 オンラインアカウントの作成には、柔軟性が非常に高くなります。 新しい Microsoft 365 サブスクリプションがある場合は、すべてのユーザーのオンラインアカウントを一括作成できます。 Microsoft 365 にオンラインアカウントを既に作成している場合は、心配は無用です。 新しいサーバーをセットアップする場合は、オンラインアカウントをインポートすることによって、サーバー上にユーザーアカウントを作成できます。 また、個々のユーザーアカウントを作成するとき、または既存のユーザーアカウントにオンラインアカウントを追加するときに、新規または既存のオンラインアカウントを割り当てることができます。

 **ライセンス要件** 作成するオンラインアカウントごとにユーザーライセンスが必要になります。 ダッシュボードの [ **Microsoft 365** ] ページで、Microsoft 365 サブスクリプションを通じて使用可能なユーザーライセンスの数を確認します。 ユーザーライセンスを追加する必要がある場合は、Microsoft 365 で Microsoft 365 サブスクリプションを開くことができます。

 **ユーザーのフォローアップ** ユーザーアカウントのオンラインアカウントを追加した後、ユーザーは次回サインインするときに、ユーザーアカウントのパスワードを変更する必要があります。 新しいパスワードは、オンライン アカウントにすぐに同期します。 その後、パスワードを使用して、オンライン ID で Microsoft 365 にサインインできます。

> [!IMPORTANT]
>  Microsoft 365 でオンラインアカウントのパスワードを変更しないようにユーザーに強調します。 パスワードは、ユーザーが自分のユーザー アカウントのパスワードを変更したときに必ず自動的に変更されます。 Microsoft 365 でオンラインパスワードを変更すると、パスワード同期が切断されます。

 このセクションに示す手順に従って、次のことを行います。

-   [既存のユーザー アカウントのオンライン アカウントを一括作成する](#BKMK_ToBulkCreateOnlineAccounts)

-   [Microsoft Online Services アカウントからユーザー アカウントをインポートする](#BKMK_ToImportUserAccounts)

-   [オンライン アカウントが割り当てられた新しいユーザー アカウントを作成する](#BKMK_ToCreateaNewUserAccount)

-   [オンライン アカウントをユーザー アカウントに割り当てる](#BKMK_ToAssignAnOnlineAccount)

> [!NOTE]
>  Windows Server Essentials を使用している場合は、これらの手順全体で*Microsoft Online Services アカウント*ではなく*Microsoft 365 アカウント*が表示されます。 このプロセスは同じですが、Windows Server Essentials では用語が変更されています。

###  <a name="to-bulk-create-online-accounts-for-your-existing-user-accounts"></a><a name="BKMK_ToBulkCreateOnlineAccounts"></a> 既存のユーザーアカウントのオンラインアカウントを一括作成するには

1.  管理者としてサーバーにサインインし、Windows Server Essentials ダッシュボードを開きます。

2.  ダッシュボードで、[**ユーザー**] ページを開きます。

3.  [**ユーザー タスク**] で、[**Microsoft Online アカウントの追加**] をクリックします。

     ウィザードの [**Microsoft Online Services アカウントの追加**] ページには、Microsoft オンライン アカウントを持っていないすべてのユーザー アカウントが表示されます。 既定ではすべてのアカウントが選択されており、Microsoft オンライン ID に対してユーザー名が提案されます。 カスタムインターネットドメインを Microsoft 365 サブスクリプションにリンクしている場合は、既定でそのドメインが使用されます。

4.  [**Microsoft Online Services アカウントの追加**] ページで、作成されるアカウントを確認します。 たとえば、オンライン ID が異なるオンライン アカウントを既に持っているユーザーがいるかどうかを確認し、電子メール アドレスで使用するドメインが選択されていることを確認します。 必要な変更作業が終了したら、**[次へ]** をクリックします。

5.  [ **Microsoft Online services ライセンスの割り当て** ] ページで、ユーザーが使用する Microsoft 365 サービスを選択します。 **[次へ]** をクリックすると、アカウントの作成が開始されます。

    > [!NOTE]
    >  オンラインアカウントごとに Microsoft 365 のサービスライセンスが必要です。 利用可能なライセンスを確認し、必要に応じてサブスクリプションを開いて、ダッシュボードの [ **Microsoft 365** ] ページからライセンスを追加することができます。

6.  Microsoft オンライン アカウントを使用できるようになったことをユーザーに通知します。 Microsoft 365 にサインインするには、ネットワークユーザーアカウントのパスワードを変更する必要があります。 手順については、「[新しい Microsoft オンライン アカウントの使用を開始する](#BKMK_ToBeginUsingAnOnlineAccount)」を参照してください。

###  <a name="to-begin-using-a-new-microsoft-online-account"></a><a name="BKMK_ToBeginUsingAnOnlineAccount"></a> 新しい Microsoft オンラインアカウントの使用を開始するには

1.  ネットワーク ユーザー アカウントを使用してコンピューターにサインインします。

2.  ユーザー アカウントのパスワードを変更します。 まず、Ctrl + Alt + Del キーを押し、次に [**パスワードの変更**] をクリックします。

     パスワードを変更すると、そのパスワードは新しいオンライン アカウントに同期されます。 同じパスワードを使用して、Microsoft 365 にサインインできるようになりました。

3.  新しいオンライン ID とユーザーアカウントのパスワードを使用して[Microsoft 365 にサインイン](https://login.microsoftonline.com/login.srf?wa=wsignin1.0&rpsnv=3&ct=1398981834&rver=6.1.6206.0&wp=MBI_SSL&wreply=https:%2F%2Foutlook.office365.com%2Fowa%2F&id=260563&CBCXT=out)します。

    > [!IMPORTANT]
    >  Microsoft 365 では、オンラインアカウントのパスワードを変更しないでください。 それを行うと、パスワード同期化が無効になります。 ネットワーク ユーザー アカウントのパスワードを変更するたびに、オンライン パスワードが更新されます。

###  <a name="to-import-user-accounts-from-your-existing-online-accounts"></a><a name="BKMK_ToImportUserAccounts"></a> 既存のオンラインアカウントからユーザーアカウントをインポートするには

1.  ダッシュボードで、[**ユーザー**] ページを開きます。

2.  [ **ユーザータスク**] で、[ **Microsoft 365 からのアカウントのインポート**] をクリックします。

     次のページには、サーバー上にユーザーアカウントを持たない Microsoft 365 サブスクリプションのオンラインアカウントがすべて表示されます。 既定ではすべてのアカウントが選択されており、ユーザー名に対してオンライン ID が提案されます。

3.  ユーザー アカウントを作成するには

    1.  提案されたユーザー アカウントに必要な変更を加えます。

    2.  必要に応じて、ユーザー アカウントに割り当てられる一時的なパスワードを表示するリンクをクリックします。 新しいアカウント名と一緒に一時パスワードをユーザーに付与する必要があります

         (アカウントを作成すると、次のファイルにこれらのパスワードが表示されます。 *SystemDrive*/Users \\*Office365admin* \\*Newserveruser*.Txt。 *Office365admin*は、サーバー上で Microsoft 365 を管理するために使用されるネットワークアカウントで、 *newserveruser*は新しいユーザーアカウント名です)。

    3.  **[次へ]** をクリックして、ユーザー アカウントを作成します。

4.  新しいユーザーアカウントと、サーバーで初めてサインインするときに使用する一時パスワードをユーザーに知らせ、サインイン後にパスワードを変更する必要があることをする。します。 ユーザー向けの手順については、「 [新しい Microsoft オンライン アカウントの使用を開始するには](#BKMK_ToBeginUsingAnOnlineAccount)」を参照してください。

     オンラインアカウントのパスワードは今後のユーザーアカウントと同期され、Microsoft 365 ではオンラインパスワードを変更しないように注意してください。

###  <a name="to-create-a-new-user-account-with-an-online-account-assigned-to-it"></a><a name="BKMK_ToCreateaNewUserAccount"></a> オンラインアカウントが割り当てられた新しいユーザーアカウントを作成するには

1.  ダッシュボードで、[**ユーザー**] をクリックします。

2.  [**ユーザー タスク**] で、[**ユーザー アカウントの追加**] をクリックします。 ユーザー アカウントの追加ウィザードが表示されます。

3.  指示に従って、ユーザー アカウントを作成します。

4.  [**Microsoft Online Services アカウントの割り当て**] ページで、ユーザー用に新しいオンライン アカウントを作成するか、または既存のオンライン アカウントを割り当てます。

    -   新しいオンライン アカウントを作成するには、[**新しい Microsoft Online Services アカウントを作成し、それをこのユーザー アカウントに割り当てる**] をクリックし、Microsoft Online Services アカウントの名前を入力します (既定では、ユーザー名はオンライン ID に使用されます)。 続けて、 **[次へ]** をクリックします。

    -   既存の Microsoft オンライン アカウントを割り当てるには、[**既存の Microsoft Online Services アカウントをこのユーザー アカウントに割り当てる**] をクリックし、ドロップダウン リストから既存のアカウントを選択します。 続けて、 **[次へ]** をクリックします。

    > [!NOTE]
    >  Windows Server Essentials では、Microsoft Online Services アカウントは、ウィザードとダッシュボードラベルで Microsoft 365 アカウントと呼ばれます。

5.  指示に従ってウィザードを完了します。

6.  新しいオンラインアカウントを使用して Microsoft 365 にサインインするには、ユーザーアカウントのパスワードを変更する必要があることをユーザーに通知します。 手順については、「[新しい Microsoft オンライン アカウントの使用を開始する](#BKMK_ToBeginUsingAnOnlineAccount)」を参照してください。

#### <a name="to-assign-an-online-account-to-a-user-account"></a><a name="BKMK_ToAssignAnOnlineAccount"></a>オンライン アカウントをユーザー アカウントに割り当てるには

1.  ダッシュボードで、[**ユーザー**] をクリックします。

2.  一覧でユーザー アカウントを右クリックし、[**Microsoft のオンライン アカウントの割り当て**] をクリックします。 Microsoft Online Services アカウントの割り当てウィザードが表示されます。

3.  既存のオンライン アカウントを割り当てるか、ユーザー用に新しいオンライン アカウントを作成します。 新しいアカウントの既定のオンライン ID は、ユーザー名です。 [**次へ**] をクリックし、オンライン アカウントをユーザー アカウントに追加します。

4.  ウィザードの最後のページにある情報を確認し、[**閉じる**] をクリックします。

5.  新しいオンラインアカウントを使用して Microsoft 365 にサインインするには、ユーザーアカウントのパスワードを変更する必要があることをユーザーに通知します。 手順については、「[新しい Microsoft オンライン アカウントの使用を開始する](#BKMK_ToBeginUsingAnOnlineAccount)」を参照してください。

##  <a name="manage-online-accounts"></a><a name="BKMK_SECTION_ManageOnlineAccounts"></a> オンラインアカウントの管理
 Windows Server Essentials でユーザーアカウントにオンラインアカウントを追加すると、アカウントのライフサイクル全体で両方のアカウントをまとめて管理できます。

###  <a name="understanding-the-online-account-status"></a><a name="BKMK_UnderstandingAccountStatus"></a> オンラインアカウントの状態について
 Microsoft Online Services アカウントをユーザー アカウントに割り当てると、ダッシュボードの [**ユーザー**] ページの [**Microsoft オンライン アカウント**] 列にアカウントの電子メール アドレスが表示されます (Windows Server Essentials では、列ラベルは **Microsoft 365 account**)。

-   電子メール アドレスの横にある青いアイコンは、オンライン アカウントがアクティブであることを示します。 つまり、アカウントには現在の Microsoft 365 ライセンスがあり、ユーザーはオンライン ID を使用して Microsoft 365 にサインインできます。

-   電子メールアドレスの横にある灰色のアイコンは、ライセンスがアクティブでなくなったか、オンラインアカウントが割り当て解除されているために、オンラインアカウントが非アクティブであることを示しています。する。 ユーザーのオンラインアカウントの割り当てを解除すると、ライセンスが削除され、ユーザーはアカウントを使用した Microsoft 365 へのサインインがブロックされます。 ただし、サーバーは、ユーザーアカウント名と Microsoft 365 電子メールアドレスとの間のマッピングを維持します。

###  <a name="restrict-access-to-an-online-account"></a><a name="BKMK_UnassignOnlineAccount"></a> オンラインアカウントへのアクセスを制限する
 ユーザーが退職した場合、またはユーザーが Microsoft 365 services にアクセスできるように制限する場合は、どうすればよいですか。 Windows Server Essentials でユーザーアカウントと共にユーザーのオンラインアカウントを管理する場合、次の3つのオプションがあります。

-   **オンラインアカウントの割り当てを解除し** ますか?サーバー上のリソースへのアクセスを防止せずに、ユーザーが Microsoft 365 を使用しないようにするには、オンラインアカウントの割り当てを解除する必要があります。 Microsoft 365 ライセンスが解放され、ユーザーは Microsoft 365 へのサインインがブロックされます。 ただし、サーバーは、ユーザーアカウント名と Microsoft 365 電子メールアドレスとの間のマッピングを維持します。 手順については、「 [ユーザーアカウントからオンラインアカウントの割り当てを解除するに](#BKMK_ToUnassignAnOnlineAccount)は」を参照してください。

-   **ユーザーアカウントを非アクティブ化し** ますか?ユーザーアカウントを非アクティブ化すると、従業員が一時的または永続的に、そのユーザーのオンラインアカウントも非アクティブになります。 オンライン アカウントは使用できませんが、ユーザーのデータ (電子メールなど) は、Microsoft Online Services に保持されます。 手順については、「 [Manage User Accounts](Manage-User-Accounts-in-Windows-Server-Essentials.md)」の「 [Deactivate a user account](Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Manage6) 」を参照してください。

-   **ユーザーアカウントを削除し** ますか?ユーザーアカウントを削除すると、オンラインアカウントも Microsoft Online Services から削除されます。 手順については、「 [Manage User Accounts](Manage-User-Accounts-in-Windows-Server-Essentials.md)」の「 [Remove a user account](Manage-User-Accounts-in-Windows-Server-Essentials.md#BKMK_Remove) 」を参照してください。

    > [!WARNING]
    >  オンライン アカウントが削除されると、ユーザー データは Microsoft Online Services のデータ保持ポリシーの影響下に置かれるので注意してください。 従業員が退職した後にユーザーデータを保持する必要がある場合は、ユーザーアカウントを削除するのではなく、非アクティブにします。

####  <a name="to-unassign-an-online-account-from-a-user-account"></a><a name="BKMK_ToUnassignAnOnlineAccount"></a> ユーザーアカウントからオンラインアカウントの割り当てを解除するには

1.  ダッシュボードで、[**ユーザー**] をクリックします。

2.  一覧でユーザーアカウントを右クリックし、[ **Microsoft オンラインアカウントの割り当て解除** ] をクリックします (Windows Server Essentials では、[ **Microsoft 365 アカウントの割り当て解除**] をクリックします)。

3.  確認のプロンプトで、[**はい**] をクリックします。

##  <a name="manage-email-addresses-for-exchange-online"></a><a name="BKMK_SECTION_ManageEmailAddresses"></a> Exchange Online の電子メールアドレスを管理する
 Windows Server Essentials でユーザーのオンラインアカウントに電子メールアドレスを追加することにより、Exchange Online の複数の電子メールアドレスでユーザーが電子メールを受信できるようにすることができます。

###  <a name="to-add-additional-email-addresses-to-a-user-s-microsoft-online-account"></a><a name="BKMK_PROC_AddEmailAliases"></a> ユーザーの Microsoft オンラインアカウントに電子メールアドレスを追加するには

1.  Windows Server Essentials ダッシュボードで、[ **ユーザー**] をクリックします。

2.  一覧でユーザー アカウントを右クリックし、[**アカウント プロパティを表示**] をクリックします。

3.  アカウントのプロパティの [ **Microsoft online** ] タブ (または Windows Server Essentials の [ **Microsoft 365** ] タブ) で、[ **追加**] をクリックします。

4.  新しい電子メールのエイリアスを入力し、電子メール ドメインを選択します。

5.  [**OK**] を 2 回クリックします。

##  <a name="manage-distribution-groups-for-exchange-online-windows-server-essentials-only"></a><a name="BKMK_SECTION_ManageDistributionGroups"></a> Exchange Online の配布グループの管理 (Windows Server Essentials のみ)
 Windows Server Essentials サーバーを Microsoft 365 と統合すると、Windows Server Essentials ダッシュボードから Exchange Online の配布グループを作成および管理できます。 この操作は、[**ユーザー** ] ページに追加された [**配布グループ**] タブで行います。 Exchange Online サブスクリプションを持っている場合は、このタブのみ表示されます。 この機能は、Windows Server Essentials では使用できません。

 以下の手順を使用して次のことを行います。

-   [配布グループを追加する](#BKMK_PROCEDURE_AddDistGroup)

-   [配布グループのメンバーを変更する](#BKMK_ChangeGroupMembers)

-   [ユーザーの配布グループのメンバーシップを変更する](#BKMK_EditUserMemberships)

-   [配布グループを削除する](#BKMK_RemoveDistributionGroup)

###  <a name="to-add-a-distribution-group"></a><a name="BKMK_PROCEDURE_AddDistGroup"></a> 配布グループを追加するには

1.  Windows Server Essentials のダッシュボードで、[ **ユーザー**] をクリックし、[ **配布グループ** ] タブをクリックします。

2.  [**配布グループ タスク**] で、[**配布グループの追加**] をクリックします。

     [新しい配布グループの追加] ウィザードが表示されます。

3.  [**新しい配布グループの追加**] ページで、次の情報を入力し、[**次へ**] をクリックします。

    -   新しい配布グループのグループ名、オプションの説明、および電子メールのエイリアスを入力します。

    -   既定では、配布グループは、組織の外部の人からの電子メールを受信できます。 これを許可しないようにする場合は、該当するオプションをオフにします。

4.  [**グループ メンバーの追加**] ページの [**追加**] ボタンを使用して、オンライン アカウントが割り当てられているアクティブなユーザー アカウント、およびその他の配布グループを、新しい配布グループに追加します。 続けて、 **[次へ]** をクリックします。

     Exchange Online で新しい配布グループが作成されます。

###  <a name="to-change-the-members-of-a-distribution-group"></a><a name="BKMK_ChangeGroupMembers"></a> 配布グループのメンバを変更するには

1.  ダッシュボードで、[**ユーザー**] をクリックし、[**配布グループ**] タブをクリックします。

2.  一覧で配布グループを右クリックし、[**グループ メンバーシップの変更**] をクリックします。

3.  [**追加**] ボタンと [**削除**] ボタンを使用し、配布グループに対してアクティブなオンライン アカウントの追加または削除を行います。 [**次へ**] をクリックし、Exchange Online で配布グループ メンバーシップを更新します。

###  <a name="to-change-a-user-s-distribution-group-memberships"></a><a name="BKMK_EditUserMemberships"></a> ユーザーの配布グループのメンバーシップを変更するには

1.  ダッシュボードで、[**ユーザー**] をクリックします。

2.  一覧でユーザー アカウントを右クリックし、[**アカウント プロパティを表示**] をクリックします。

3.  ユーザー アカウント プロパティで、[**配布グループ**] タブをクリックし、[**編集**] をクリックします。

4.  [**グループ メンバーシップの編集**] ボックスの [**追加**] ボタンと [**削除**] ボタンを使用し、ユーザー アカウントに対して配布グループの追加または削除を行い、[**閉じる**] をクリックします。

5.  [**OK**] をクリックして、更新済のユーザー アカウント プロパティを保存します。

###  <a name="to-remove-a-distribution-group"></a><a name="BKMK_RemoveDistributionGroup"></a> 配布グループを削除するには

1.  ダッシュボードで、[**ユーザー**] をクリックし、[**配布グループ**] タブをクリックします。

2.  一覧で配布グループを右クリックし、[**グループの削除**] をクリックします。

3.  確認のプロンプトで、[**グループの削除**] をクリックします。

     配布グループが Exchange Online から削除されます。

## <a name="additional-references"></a>その他の参照情報

-   [ユーザー アカウントの管理](Manage-User-Accounts-in-Windows-Server-Essentials.md)

-   [Microsoft 365 の管理](Manage-Office-365-in-Windows-Server-Essentials.md)

-   [Microsoft Online Services の管理](Manage-Microsoft-Online-Services-in-Windows-Server-Essentials.md)
