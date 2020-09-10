---
title: list shadows
description: '[シャドウの一覧表示] コマンドの参照記事。システム上の永続的なシャドウコピーと永続的でないシャドウコピーが一覧表示されます。'
ms.topic: reference
ms.assetid: fe568423-00ae-4ede-a1e7-07977cb50ad1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4781587fd7bb82525746184c3fee2f0f9258c510
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635269"
---
# <a name="list-shadows"></a>list shadows

システム上の永続的なシャドウコピーと永続的でないシャドウコピーを一覧表示します。

## <a name="syntax"></a>構文

```
list shadows {all | set <setID> | id <shadowID>}
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---------- | ---------- |
| all | すべてのシャドウコピーを一覧表示します。 |
| 一連 `<setID>` | 指定されたシャドウコピーセット ID に属するシャドウコピーを一覧表示します。 |
| 番号 `<shadowID>` | 指定されたシャドウコピー ID を持つシャドウコピーを一覧表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)