---
title: 紹介におけるターゲットの順序指定方法を設定する
description: この記事では、紹介におけるターゲットの順序指定方法を設定する方法について説明します。
ms.date: 6/5/2017
ms.prod: windows-server-threshold
ms.technology: storage
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 06e7aa1309b453da649537d5ae9b22acce830530
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59816863"
---
# <a name="set-the-ordering-method-for-targets-in-referrals"></a>紹介におけるターゲットの順序指定方法を設定する

> 適用対象:Windows Server 2019、Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

紹介とは、ユーザーが名前空間のルートにアクセスするか、ターゲットを持つフォルダーにアクセスしたときに、クライアント コンピューターがドメイン コントローラーまたは名前空間サーバーから受信する、順序付きのターゲット一覧です。 クライアントは、紹介を受信した後、一覧の先頭のターゲットにアクセスしようとします。 そのターゲットにアクセスできない場合は、次のターゲットにアクセスしようとします。
クライアント サイト上のターゲットは常に紹介の最初にリストされます。 クライアント サイト外のターゲットは、順序指定方法に従ってリストされます。

以降のセクションでは、ターゲットをクライアントに紹介する順序を指定し、ターゲット紹介の順序を指定するさまざまな方法について理解します。

## <a name="to-set-the-ordering-method-for-targets-in-namespace-root-referrals"></a>名前空間ルートの紹介におけるターゲットの順序指定方法を設定するには

名前空間ルートにおける順序指定方法を設定するには、次の手順を使用します。

1.  **[スタート]** をクリックし、**[管理ツール]** をポイントして、**[DFS 管理]** をクリックします。

2.  コンソール ツリーの **[名前空間]** ノードで、名前空間を右クリックし、**[プロパティ]** をクリックします。

3.  **[紹介]** タブで、順序指定方法を選択します。

> [!NOTE]
> Windows PowerShell を使って名前空間ルートの紹介におけるターゲットの順序指定方法を設定するには、次のいずれかのパラメーターを指定して [Set-DfsnRoot](https://technet.microsoft.com/library/jj884281.aspx) コマンドレットを使います。
   -   **EnableSiteCosting** の場合、**"最低コストの順序指定"** の方法が指定されます。
   -   **EnableInsiteReferrals** の場合、**"クライアント サイト外のターゲットを除外する"** 順序指定方法が指定されます。
   -   いずれかのパラメーターを省略すると、**"ランダム順序"** の参照順序指定方法が指定されます。 

DFSN の Windows PowerShell モジュールは、Windows Server 2012 で導入されました。
   
## <a name="to-set-the-ordering-method-for-targets-in-folder-referrals"></a>フォルダー紹介におけるターゲットの順序指定方法を設定するには

ターゲットを持つフォルダーは、名前空間ルートからの順序指定方法を継承します。 順序指定方法は、次の手順を使用して上書きできます。

1.  **[スタート]** をクリックし、**[管理ツール]** をポイントして、**[DFS 管理]** をクリックします。

2.  コンソール ツリーの **[名前空間]** ノードで、ターゲットを持つフォルダーを右クリックし、**[プロパティ]** をクリックします。

3.  **[紹介]** タブで、**[クライアント サイト外のターゲットを除外する]** チェック ボックスをオンにします。

> [!NOTE]
> Windows PowerShell を使ってクライアント サイト外のフォルダー ターゲットを除外するには、[Set-DfsnFolder –EnableInsiteReferrals](https://technet.microsoft.com/library/jj884283.aspx) コマンドレットを使います。

## <a name="target-referral-ordering-methods"></a>ターゲット紹介の順序指定方法

3 つの順序指定方法は次のとおりです。

-   ランダム順序
-   最低コスト
-   クライアント サイト外のターゲットを除外する

## <a name="random-order"></a>ランダム順序

この方法では、ターゲットが次のように順序指定されます。

1.  クライアントと同じ Active Directory ディレクトリ サービス (AD DS) サイトのターゲットには、紹介の最上部に無作為な順序で表示されます。
2.  クライアント サイト外部のターゲットは、ランダムな順序でリストされます。

同じサイトのターゲット サーバーがない場合、クライアント コンピューターは、接続のコストやターゲットとの距離に関係なくランダムなターゲット サーバーに紹介されます。

## <a name="lowest-cost"></a>最低コスト

この方法では、ターゲットが次のように順序指定されます。

1.  クライアントと同じサイト内のターゲットは、紹介の一番上にあるランダムな順序でリストされます。
2.  クライアント サイト外のターゲットは、コストが低い順にリストされます。 同じコストの紹介は一緒にグループ化され、ターゲットはグループごとにランダムな順序でリストします。

> [!NOTE]
> サイト リンクのコストは、DFS 管理スナップインに表示されません。 サイト リンクのコストを表示するには、Active Directory サイトとサービス スナップインを使います。

## <a name="exclude-targets-outside-of-the-clients-site"></a>クライアント サイト外のターゲットを除外する

この方法では、クライアントと同じサイト内のターゲットのみ紹介に含まれます。 これらの同じサイトのターゲットは、ランダムな順序でリストされます。 同じサイトのターゲットが存在しない場合、クライアントは紹介を受け取らず、名前空間の部分にアクセスできません。

> [!NOTE]
> 順序指定方法が **[クライアント サイト外のターゲットを除外する]** に設定されている場合でも、ターゲット優先順位が [すべてのターゲットのうち最初のターゲット] または [すべてのターゲットのうち最後のターゲット] に設定されたターゲットは紹介にリストされます。

## <a name="see-also"></a>関連項目 

-   [DFS 名前空間のチューニング](tuning-dfs-namespaces.md)
-   [Delegate Management Permissions for DFS 名前空間](delegate-management-permissions-for-dfs-namespaces.md)