---
title: bitsadmin list
description: Bitsadmin list コマンドの参照記事。現在のユーザーが所有している転送ジョブの一覧が表示されます。
ms.topic: reference
ms.assetid: 1416965e-e0e6-49cf-b1d4-b286d3cf8716
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e1d36a9236c834cea76e653b9a2e639c3b8f964e
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024376"
---
# <a name="bitsadmin-list"></a>bitsadmin list

現在のユーザーが所有している転送ジョブの一覧を表示します。

## <a name="syntax"></a>構文

```
bitsadmin /list [/allusers][/verbose]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| /allusers | 省略可能。 すべてのユーザーのジョブを一覧表示します。 このパラメーターを使用するには、管理者特権が必要です。 |
| /verbose | 省略可能。 各ジョブの詳細情報を提供します。 |

## <a name="examples"></a>例

現在のユーザーが所有しているジョブに関する情報を取得します。

```
bitsadmin /list
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
