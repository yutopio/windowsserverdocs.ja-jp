---
description: 詳細については、展開の計画に関するページを参照してください。
ms.assetid: bb9b9e18-bf2f-4115-be77-9a165944db41
title: 展開の計画
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: cf87eb0407ae963d74d90696ed46b90e9e5152b7
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97040410"
---
# <a name="planning-your-deployment"></a>展開の計画

\- \( Active Directory フェデレーションサービス (AD FS) AD FS を使用して組織間のフェデレーションに基づくコラボレーションを計画する場合 \- \) \( \) は、まず、組織がインターネットを介して他の組織からアクセスする web リソースをホストするか、組織内の従業員の web リソースへのアクセスを提供するかを決定します。 この決定は、AD FS の展開方法に影響を与えると共に、AD FS インフラストラクチャの計画の基礎になります。

> [!NOTE]
> 組織がフェデレーション契約で果たす役割をすべての当事者が明確に理解するようにしてください。

[フェデレーション WEB SSO 設計](Federated-Web-SSO-Design.md)では、AD FS は、AD FS 管理スナップインでは id プロバイダーとも呼ばれる *アカウントパートナー* \( や、リソースパートナーの \- \)  \(  \- \) \( \) web ベースリソースをホストする組織からアカウントパートナーをホストする組織を区別するためにリソース \- \( AD FS パートナー \) と呼ばれるリソースパートナーなどの用語を使用します。

[Web SSO Design](Web-SSO-Design.md)では、組織はユーザーに対してアプリケーションへのアクセスを提供するため、アカウント パートナーとリソース パートナー両方の役割を実行します。

次のトピックでは、AD FS パートナー組織の概念について説明します。 また、AD FS の展開目標に基づいてアカウントパートナー組織およびリソースパートナー組織のセットアップと構成に関する情報が記載されている、AD FS 展開ガイドのトピックへのリンクも含まれています。

## <a name="in-this-section"></a>このセクションの内容

-   [AD FS のセキュリティを考慮した設計と展開のベスト プラクティス](Best-Practices-for-Secure-Planning-and-Deployment-of-AD-FS.md)

-   [AD FS 1.x との相互運用性の計画](Planning-for-Interoperability-with-AD-FS-1.x.md)

-   [Id 委任を使用する場合](When-to-Use-Identity-Delegation.md)

-   [アカウント パートナー組織での AD FS の展開](Deploying-AD-FS-in-the-Account-Partner-Organization-2012.md)

-   [リソース パートナー組織での AD FS の展開](Deploying-AD-FS-in-the-Resource-Partner-Organization-2012.md)

## <a name="see-also"></a>関連項目
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)


