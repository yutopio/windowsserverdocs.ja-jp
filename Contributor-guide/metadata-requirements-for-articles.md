---
title: Windows Server 関連の記事に必要なメタデータタグを追加する
description: Windows Server 関連の記事の上部にメタデータタグとして追加する必要がある情報の一覧。 必要なタグは、レポートとチームの両方の要件に基づいて変更される可能性があります。
author: eross-msft
ms.author: lizross
ms.date: 05/06/2019
ms.openlocfilehash: 7728d6e9bb2c1e5a6ad53f638f253c53a0720059
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91717749"
---
# <a name="add-the-required-metadata-tags-to-your-windows-server-related-article"></a>Windows Server 関連の記事に必要なメタデータタグを追加する

各記事の上部には、追跡と SEO の目的で特定のメタデータが含まれている必要があります。 必要なタグは、レポートの要件に基づいて変更される可能性があります。 ただし、フィールドを追加または削除する必要がある場合は通知されます。

次のようになります。上部と下部にある3つのハイフン (---) を含みます。

```markdown
---
title: Required. The title of the article should go here. This is used in SEO and search results.
description: Required. A description for the article should go here. This is used in search results, to provide users with information about whether the article has the information they're looking for.
author: Required. Your GitHub alias
ms.author: Required. Your Microsoft alias
manager: Optional. Your manager's Microsoft alias
ms.reviewer: Optional. The Microsoft alias for the primary PM for the feature/functionality
ms.topic: Type of article, including conceptual, how-to, hub-page, overview, quickstart, reference, sample, troubleshooting, or tutorial
ms.date: Date of change (MM/DD/YYYY)

---
```

## <a name="example"></a>例

```markdown
---
title: What is Windows Admin Center?
description: Learn about the Windows Admin Center, a locally-deployed, browser-based management tool set that lets you manage your Windows Servers with no Azure or cloud dependency.
author: danielle-github
ms.author: danielle
manager: alainch
ms.reviewer: alainch
ms.topic: overview
ms.date: 07/06/2019

---
```