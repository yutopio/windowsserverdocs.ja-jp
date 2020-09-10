---
title: bitsadmin cache と deleteURL
description: Bitsadmin cache および deleteURL コマンドのリファレンス記事。指定された URL のすべてのキャッシュエントリを削除します。
ms.topic: reference
ms.assetid: e108b76b-fae9-4c16-bf4c-d74c9f025953
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6e1c3af4cfbb6c1ef21a86ead6d3975bf1f44cf6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632623"
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
