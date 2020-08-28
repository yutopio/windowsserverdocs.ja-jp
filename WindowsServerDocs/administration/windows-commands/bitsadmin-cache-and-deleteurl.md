---
title: bitsadmin cache と deleteURL
description: Bitsadmin cache および deleteURL コマンドのリファレンス記事。指定された URL のすべてのキャッシュエントリを削除します。
ms.topic: reference
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ed804580c4435b612b91875ef59cf6eb8ca4275b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026710"
---
# <a name="bitsadmin-cache-and-deleteurl"></a>bitsadmin cache と deleteURL

指定された URL のすべてのキャッシュエントリを削除します。

## <a name="syntax"></a>構文

```
bitsadmin /deleteURL URL
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| URL | リモートファイルを識別する Uniform Resource Locator。 |

## <a name="examples"></a>例

次のすべてのキャッシュエントリを削除するには `https://www.contoso.com/en/us/default.aspx` :

```
bitsadmin /deleteURL https://www.contoso.com/en/us/default.aspx
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin cache コマンド](bitsadmin-cache.md)
