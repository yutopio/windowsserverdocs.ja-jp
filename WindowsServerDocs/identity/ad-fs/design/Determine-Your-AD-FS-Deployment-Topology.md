---
description: '詳細情報: AD FS デプロイトポロジを決定する'
ms.assetid: f67b0bc9-e5af-4891-9da0-d9be539af42d
title: AD FS 展開トポロジの決定
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 1c5bd925318a6f18513fa7267c2dfe2ab5381281
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97047700"
---
# <a name="determine-your-ad-fs-deployment-topology"></a>AD FS 展開トポロジの決定

Active Directory フェデレーションサービス (AD FS) AD FS の展開を計画するための最初の手順 \( \) は、 \- 組織のシングルサインオン SSO のニーズを満たす適切な展開トポロジを決定することです \( \) 。 このセクションのトピックでは、AD FS で使用できるさまざまな展開トポロジについて説明します。 また、特定のビジネスのニーズに最適なトポロジを選択できるよう、各展開トポロジに関連する利点と制約事項についても説明します。

この展開トポロジに関するトピックを読む前に、まず次の表に示したタスクを記載された順に実行することをお勧めします。

|推奨されるタスク|説明|リファレンス|
|--------------------|---------------|-------------|
|フェデレーションサーバーファーム内の他のフェデレーションサーバーに AD FS データを格納し、レプリケートする方法を確認します。|AD FS 構成データベースに保存されている基になるデータの目的と使用可能なレプリケーション方法について理解します。 このトピックでは、構成データベースの概念について説明し、Windows Internal Database \( WID と Microsoft SQL Server という2つのデータベースの種類について説明し \) ます。|[AD FS 構成データベースの役割](../../ad-fs/technical-reference/The-Role-of-the-AD-FS-Configuration-Database.md)|
|組織で展開する AD FS 構成データベースの種類を選択する。|AD FS 構成データベースとして WID または SQL Server のどちらかを使用することに関連するさまざまな利点および制約事項と、データベースでサポートされるさまざまな利用シナリオを確認します。|[AD FS 展開トポロジに関する考慮事項](AD-FS-Deployment-Topology-Considerations.md)|

> [!NOTE]
> 基本的な冗長性、負荷分散、および必要に応じてフェデレーションサービスを拡張するオプションを実装するには、 \( \) 使用するデータベースの種類に関係なく、すべての運用環境のフェデレーションサーバーファームごとに少なくとも2台のフェデレーションサーバーを展開することをお勧めします。

前述の表の内容を確認したら、このセクションの次のトピックに進んでください。

-   [WID を使用するスタンドアロン フェデレーション サーバー](Stand-Alone-Federation-Server-Using-WID.md)

-   [WID を使用するフェデレーション サーバー ファーム](Federation-Server-Farm-Using-WID-2012.md)

-   [WID とプロキシを使用するフェデレーション サーバー ファーム](Federation-Server-Farm-Using-WID-and-Proxies-2012.md)

-   [SQL Server を使用するフェデレーション サーバー ファーム](Federation-Server-Farm-Using-SQL-Server-2012.md)

AD FS 展開トポロジの選択が完了したら、トピック「 [AD FS サーバー容量の計画](Planning-for-AD-FS-Server-Capacity.md) 」を参照して、このトポロジをサポートするために展開する必要があるサーバーの推奨数を決定することをお勧めします。

## <a name="see-also"></a>関連項目
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)

