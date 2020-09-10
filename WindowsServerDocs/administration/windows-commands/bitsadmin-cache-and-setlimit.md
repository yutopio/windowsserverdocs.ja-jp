---
title: bitsadmin cache および setlimit
description: キャッシュサイズの制限を設定する bitsadmin cache および setlimit コマンドの参照記事。
ms.topic: reference
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7547a2a51104285b10af6b02c1962c89f75d51fa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632485"
---
# <a name="bitsadmin-cache-and-setlimit"></a>bitsadmin cache および setlimit

キャッシュサイズの制限を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /cache /setlimit percent
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| パーセント | ハードディスクの合計領域に対する割合として定義されているキャッシュの制限。 |

## <a name="examples"></a>例

キャッシュサイズの制限を50% に設定するには、次のようにします。

```
bitsadmin /cache /setlimit 50
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin cache コマンド](bitsadmin-cache.md)
