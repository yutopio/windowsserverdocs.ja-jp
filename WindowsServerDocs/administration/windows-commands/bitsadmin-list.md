---
title: bitsadmin list
description: Bitsadmin list コマンドの参照記事。現在のユーザーが所有している転送ジョブの一覧が表示されます。
ms.topic: reference
ms.assetid: 1416965e-e0e6-49cf-b1d4-b286d3cf8716
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 81fecf15f16cfa28933b63f9de693ba4e07679e8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631503"
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
