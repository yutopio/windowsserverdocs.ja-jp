---
title: 手順 5 DC1 を構成する
description: このトピックは、「Windows Server 2016 用の DirectAccess マルチサイト展開のテストラボガイド」の一部です。
manager: brianlic
ms.topic: article
ms.assetid: 70357156-fcb0-4346-a61e-4ea963e3ffb0
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 165db880f36f4cf4559d746ed99f7e6a2d87c21d
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969159"
---
# <a name="step-5-configure-dc1"></a>手順 5 DC1 を構成する

>適用先:Windows Server (半期チャネル)、Windows Server 2016

DC1 は、corp.contoso.com ドメインのドメインコントローラー、DNS サーバー、および DHCP サーバーとして機能します。

マルチサイトトポロジを使用するようにリモートアクセスを構成するには、2つ目のドメインコントローラー 2 ~ DC1 の Active Directory Domain Services (AD DS) サイトを追加し、サブネット間のルーティングを構成する必要があります。

1. ドメインコントローラーで既定のゲートウェイを構成するには DC1 で既定のゲートウェイを構成します。

2. DC1 で Windows 7 DirectAccess クライアントのセキュリティグループを作成します。 DirectAccess を構成すると、DirectAccess クライアントとサーバーに適用されるグループポリシーオブジェクト (Gpo) と GPO 設定が自動的に作成されます。 DirectAccess クライアント GPO は、特定の Active Directory セキュリティグループに適用されます。

3. 新しい AD DS サイトを追加するには 2つ目の AD DS サイトを作成します。

## <a name="to-configure-the-default-gateway-on-the-domain-controller"></a>ドメインコントローラーで既定のゲートウェイを構成するには

1.  サーバーマネージャーコンソールで、[**ローカルサーバー**] をクリックし、[**プロパティ**] 領域の [**ワイヤード (有線) イーサネット接続**] の横にあるリンクをクリックします。

2.  [ネットワーク接続] ウィンドウで、[**ワイヤード (イーサネット) 接続**] を右クリックし、[**プロパティ**] をクリックします。

3.  **[インターネット プロトコル バージョン 4 (TCP/IPv4)]** をクリックし、**[プロパティ]** をクリックします。

4.  [**デフォルトゲートウェイ**] に「 **10.0.0.254**」と入力し、[**代替 DNS サーバー**] に「 **10.2.0.1**」と入力して、[ **OK]** をクリックします。

5.  **[インターネット プロトコル バージョン 6 (TCP/IPv6)]** をクリックし、**[プロパティ]** をクリックします。

6.  [**デフォルトゲートウェイ**] で、「 **2001: db8: 1:: fe**」と入力し、[**代替 DNS サーバー**] に「 **2001: db8: 2:: 1**」と入力して、[ **OK]** をクリックします。

7.  [**ワイヤード (有線) イーサネット接続のプロパティ**] ダイアログボックスで、[**閉じる**] をクリックします。

8.  **[ネットワーク接続]** ウィンドウを閉じます。

## <a name="create-security-groups-for-windows-7-directaccess-clients-on-dc1"></a>DC1 で Windows 7 DirectAccess クライアントのセキュリティグループを作成する
次の手順に従って、Windows 7 の DirectAccess セキュリティグループを作成します。

 Windows 7 のクライアントコンピューターは、1つのエントリポイントのみで内部リソースに接続できるため、個別のセキュリティグループのメンバーである必要があります。 マルチサイトサポートを有効にする場合、またはエントリポイントを追加する場合、Windows 7 のサポートが要求されると、各エントリポイントの Windows 7 クライアントの DirectAccess によって個別の GPO が自動的に作成されます。

### <a name="create-security-groups"></a>セキュリティ グループを作成する

1.  **開始** 画面で「**dsa.msc**, 、ENTER キーを押します。

2.  左側のウィンドウで、[ **corp.contoso.com**] を展開し、[ **users**] をクリックします。次に、[ **users**] を右クリックして [**新規作成**] をポイントし、[**グループ**] をクリックします。

3.  [**新しいオブジェクト-グループ**] ダイアログボックスの [**グループ名**] に、「 **Win7_Clients_Site1**」と入力します。

4.  [**グループのスコープ**] の下で [**グローバル**] をクリックし、[**グループの種類**] の下で [**セキュリティ**] をクリックし、[**OK**] をクリックします。

5.  **Win7_Clients_Site1**セキュリティグループをダブルクリックし、[Win7_Clients_Site1 の**プロパティ**] ダイアログボックスで、[**メンバー** ] タブをクリックします。

6.  [**メンバー**] タブで [**追加**] をクリックします。

7.  [**ユーザー、連絡先、コンピューター、またはサービスアカウントの選択**] ダイアログボックスで、[**オブジェクトの種類**] をクリックします。 [**オブジェクトの種類**] ダイアログボックスで、[**コンピューター**] を選択し、[ **OK**] をクリックします。

8.  [**選択するオブジェクト名を入力してください**] ボックスに「「」**と入力し、[** **ok**] をクリックします。次に、[ **Win7_Clients_Site1 のプロパティ**] ダイアログボックスで [ **ok]** をクリックします。

9. **Active Directory ユーザーとコンピューター** ] コンソールの左側のウィンドウで、[ **users**] を右クリックし、[**新規作成**] をポイントして、[**グループ**] をクリックします。

10. [**新しいオブジェクト-グループ**] ダイアログボックスの [**グループ名**] に、「 **Win7_Clients_Site2**」と入力します。

11. [**グループのスコープ**] の下で [**グローバル**] をクリックし、[**グループの種類**] の下で [**セキュリティ**] をクリックし、[**OK**] をクリックします。

12. **[Active Directory ユーザーとコンピューター]** コンソールを閉じます。

## <a name="to-add-a-new-ad-ds-site"></a>新しい AD DS サイトを追加するには

1.  **スタート**画面で、「**dssite .msc**」と入力し、enter キーを押します。

2.  コンソール ツリーで、Active Directory サイトとサービス コンソールで、右クリック **サイト**, 、クリックして **新しいサイト**します。

3.  [**新しいオブジェクト-サイト**] ダイアログボックスで、[**名前**] ボックスに「 **Second-site**」と入力します。

4.  リストボックスで、 **Defaul[サイトのリンク**] をクリックし、[ **OK** ] を2回クリックします。

5.  コンソール ツリーで [ **サイト**, を右クリックして **サブネット**, 、クリックして **新しいサブネット**します。

6.  [**新しいオブジェクト-サブネット**] ダイアログボックスの **[プレフィックス**] に「 **10.0.0.0/24**」と入力し、[**このプレフィックスのサイトオブジェクトを選択**してください] の一覧で [**既定-最初のサイト名**] をクリックし、[ **OK**] をクリックします。

7.  コンソールツリーで、[**サブネット**] を右クリックし、[**新しいサブネット**] をクリックします。

8.  [**新しいオブジェクト-サブネット**] ダイアログボックスの **[プレフィックス**] に「 **2001: db8: 1::/64**」と入力し、[**このプレフィックスのサイトオブジェクトを選択**します] の一覧で [**既定-最初のサイト名**] をクリックし、[ **OK**] をクリックします。

9. コンソールツリーで、[**サブネット**] を右クリックし、[**新しいサブネット**] をクリックします。

10. [**新しいオブジェクト-サブネット**] ダイアログボックスの **[プレフィックス**] に「 **10.2.0.0/24**」と入力し、[**このプレフィックスのサイトオブジェクトを選択**してください] の一覧で [ **2 番目のサイト**] をクリックし、[ **OK**] をクリックします。

11. コンソールツリーで、[**サブネット**] を右クリックし、[**新しいサブネット**] をクリックします。

12. [**新しいオブジェクト-サブネット**] ダイアログボックスの **[プレフィックス**] に「 **2001: db8: 2::/64**」と入力し、[**このプレフィックスのサイトオブジェクトを選択**] の一覧で [ **2 番目のサイト**] をクリックし、[ **OK**] をクリックします。

13. [Active Directory サイトとサービス] を閉じます。



