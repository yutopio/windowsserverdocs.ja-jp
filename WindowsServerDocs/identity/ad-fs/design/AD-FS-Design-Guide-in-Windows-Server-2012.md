---
description: 詳細については、「Windows Server の従来のデザインガイド AD FS」を参照してください。
ms.assetid: bb16e39d-566d-436c-b957-394c06d556db
title: Windows Server 2012 での AD FS 設計ガイド
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 88dd9ed3fcda48b1f8d93a4518cf6767431fe43f
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97042140"
---
# <a name="ad-fs-legacy-design-guide-in-windows-server"></a>Windows Server の従来のデザインガイド AD FS



> [!NOTE]
> Windows Server 2012 R2 で AD FS を展開する方法の詳細については、「 [Windows server 2012 r2 AD FS 展開ガイド](../../ad-fs/deployment/Windows-Server-2012-R2-AD-FS-Deployment-Guide.md)」を参照してください。

フェデレーションサービスプロバイダーの &reg; \( \) 役割で Windows Server 2012 オペレーティングシステムと共に Active Directory フェデレーションサービス AD FS を使用 &reg; する \- と、リソースパートナー組織に存在する Web ベースのサービスまたはアプリケーションに対してユーザーをシームレスに認証できます。管理者は、両方の組織のネットワーク間で外部の信頼またはフォレストの信頼を作成または管理する必要がなく、ユーザーが2回 別のネットワーク内のリソースにアクセスするときに、ユーザーによるログオン操作が繰り返されるのではなく、1つのネットワークに対して認証を行うプロセスは、シングルサインオン SSO と呼ばれ \- \( \) ます。

## <a name="about-this-guide"></a>このガイドについて
このガイドでは、AD FS の新しい展開を計画する際に役立つ推奨事項について説明し \( ます。このガイドでは、このガイドでは、展開の目標と、作成する特定の設計とも呼ばれ \) ます。 このガイドの対象読者は、インフラストラクチャ専門家またはシステム アーキテクトです。 AD FS の展開を計画する際に、主な意思決定点に焦点を当てます。 このガイドを読む前に、AD FS が機能レベルでどのように機能するかについて十分に理解しておく必要があります。 また、AD FS の設計に反映される組織の要件について十分に理解している必要があります。

このガイドでは、3つの主要な AD FS 設計に基づいた一連の展開目標について説明します。また、環境に最適な設計を決定するのに役立ちます。 これらの展開目標を使用して、次の包括的な AD FS 設計のいずれかを作成したり、環境のニーズを満たすカスタム設計を作成したりすることができます。

-   企業 \- \- \( \) 間 B2B シナリオをサポートし、独立したフォレストを持つ事業単位間のコラボレーションをサポートするためのフェデレーション Web SSO

-   B2c シナリオにおける顧客のアプリケーションへのアクセスをサポートするための Web SSO \- \- \( \)

それぞれの設計について、環境に関して必要なデータを収集するガイドラインが示されています。 その後、これらのガイドラインを使用して、AD FS 展開の計画と設計を行うことができます。 このガイドを読み、組織の要件の収集、文書化、マッピングを完了すると、「 [Windows Server 2012 AD FS 展開ガイド](../../ad-fs/deployment/Windows-Server-2012-AD-FS-Deployment-Guide.md)」のガイダンスに従って AD FS の展開を開始するために必要な情報が得られます。

## <a name="in-this-guide"></a>このガイドの内容

-   [AD FS 展開目標の特定](Identifying-Your-AD-FS-Deployment-Goals.md)

-   [展開目標の AD FS 設計への反映](Mapping-Your-Deployment-Goals-to-an-AD-FS-Design.md)

-   [AD FS 展開トポロジの決定](Determine-Your-AD-FS-Deployment-Topology.md)

-   [展開の計画](Planning-Your-Deployment.md)

-   [フェデレーション サーバーの配置の計画](Planning-Federation-Server-Placement.md)

-   [フェデレーション サーバー プロキシの配置の計画](Planning-Federation-Server-Proxy-Placement.md)

-   [AD FS サーバーの容量計画](Planning-for-AD-FS-Server-Capacity.md)

-   [付録 A: AD FS 要件の確認](Appendix-A--Reviewing-AD-FS-Requirements.md)


