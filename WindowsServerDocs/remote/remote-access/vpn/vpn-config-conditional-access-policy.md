---
title: 条件付きアクセス ポリシーを構成する
description: ルート証明書が作成されると、"VPN 接続" によって、顧客のテナントに "VPN サーバー" クラウドアプリケーションの作成がトリガーされます。
ms.topic: article
ms.date: 05/25/2018
ms.author: v-tea
author: Teresa-MOTIV
ms.localizationpriority: medium
ms.reviewer: deverette
ms.openlocfilehash: 7535de9f11a8daf38ad1aab2fe95a620f9682025
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87946705"
---
# <a name="step-73-configure-the-conditional-access-policy"></a>手順 7.3.  条件付きアクセス ポリシーを構成する

>適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows 10

- [**前へ:** 手順 7.2.Azure AD を使用した VPN 認証用のルート証明書の作成](vpn-create-root-cert-for-vpn-auth-azure-ad.md)
- [**次のようになります。** 手順 7.4.条件付きアクセスルート証明書をオンプレミスの AD にデプロイする](vpn-deploy-cond-access-root-cert-to-on-premise-ad.md)

この手順では、VPN 接続の条件付きアクセスポリシーを構成します。 [VPN 接続] ブレードに最初のルート証明書が作成されると、"VPN サーバー" クラウドアプリケーションがテナントに自動的に作成されます。

VPN ユーザーグループに割り当てられている条件付きアクセスポリシーを作成し、**クラウドアプリ**を**vpn サーバー**にスコープを指定します。

- **ユーザー**: VPN ユーザー
- **クラウドアプリ**: VPN サーバー
- **Grant (アクセス制御)**: ' Multi-factor Authentication が必要です '。 必要に応じて、他のコントロールを使用できます。

**手順:** この手順では、最も基本的な条件付きアクセスポリシーの作成について説明します。必要に応じて、追加の条件とコントロールを使用できます。


1. [**条件付きアクセス**] ページの上部にあるツールバーで、[**追加**] を選択します。

    ![[条件付きアクセス] ページで [追加] を選択](../../media/Always-On-Vpn/07.png)

2. [**新規**] ページの [**名前**] ボックスに、ポリシーの名前を入力します。 たとえば、「 **VPN ポリシー**」と入力します。

    ![[条件付きアクセス] ページでポリシーの名前を追加](../../media/Always-On-Vpn/08.png)

3. [**割り当て**] セクションで、[**ユーザーとグループ**] を選択します。

    ![ユーザーとグループを選択](../../media/Always-On-Vpn/09.png)

4. **[ユーザーとグループ]** ページで、次の手順を実行します。

    ![テスト ユーザーを選択](../../media/Always-On-Vpn/10.png)

    a. [**ユーザーとグループの選択**] を選択します。

    b. **[選択]** を選択します。

    c. [**選択**] ページで、[ **VPN ユーザー** ] グループを選択し、[**選択**] を選択します。

    d. [**ユーザーとグループ**] ページで、[**完了**] を選択します。

5. **[新規]** ページで、次の手順を実行します。

    ![クラウド アプリを選択](../../media/Always-On-Vpn/11.png)

    a. [**割り当て**] セクションで、[**クラウドアプリ**] を選択します。

    b. [**クラウドアプリ**] ページで、[**アプリの選択**] を選択します。

    d. **[VPN サーバー]** を選択します。

6.  [**新規**] ページで [**許可**] ページを開くには、[**コントロール**] セクションで [**許可**] を選択します。

    ![[許可] を選択](../../media/Always-On-Vpn/13.png)

7.  **[許可]** ページで、次の手順を実行します。

    ![[多要素認証が必要です] を選択](../../media/Always-On-Vpn/14.png)

    a. **[多要素認証が必要]** を選択します。

    b. **[選択]** を選択します。

8.  [**新規**] ページの [**ポリシーの有効化**] で、[**オン**] を選択します。

    ![ポリシーを有効にする](../../media/Always-On-Vpn/15.png)

9.  [**新規**] ページで、[**作成**] を選択します。


## <a name="next-steps"></a>次のステップ
[手順 7.4.条件付きアクセスルート証明書をオンプレミスの AD にデプロイ](vpn-deploy-cond-access-root-cert-to-on-premise-ad.md)する: この手順では、条件付きアクセスルート証明書を VPN 認証用の信頼されたルート証明書としてオンプレミスの ad にデプロイします。
