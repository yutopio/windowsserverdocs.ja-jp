---
title: bitsadmin cache および setlimit
description: キャッシュサイズの制限を設定する bitsadmin cache および setlimit コマンドの参照記事。
ms.topic: reference
ms.assetid: 46578835-d5ce-423b-be4d-62ddb9e1908d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: edcd83ace72e301471b03ac0c1fc85439a1c4d94
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028790"
---
# <a name="bitsadmin-cache-and-setlimit"></a>bitsadmin cache および setlimit

キャッシュサイズの制限を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /cache /setlimit percent
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
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
