---
title: delete shadows
description: シャドウコピーを削除するシャドウコピーコマンドの参照記事。
ms.topic: reference
ms.assetid: e29a84d2-04d1-4eb1-910a-5a47bddbc24d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d2613fc978db8c8e5b323df142b204a7270f6bad
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024206"
---
# <a name="delete-shadows"></a>delete shadows

シャドウコピーを削除します。

## <a name="syntax"></a>構文

```
delete shadows [all | volume <volume> | oldest <volume> | set <setID> | id <shadowID> | exposed {<drive> | <mountpoint>}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---- | ---- |
| all | すべてのシャドウコピーを削除します。 |
| 体積 `<volume>` | 指定されたボリュームのシャドウコピーをすべて削除します。 |
| 方 `<volume>` | 指定されたボリュームの最も古いシャドウコピーを削除します。 |
| 一連 `<setID>` | 指定された ID のシャドウコピーセットに含まれるシャドウコピーを削除します。 別名が現在の環境に存在する場合は、シンボルを使用してエイリアスを指定でき **%** ます。 |
| 番号 `<shadowID>` | 指定された ID のシャドウコピーを削除します。 別名が現在の環境に存在する場合は、シンボルを使用してエイリアスを指定でき **%** ます。 |
| 公開された {'<drive> | <mountpoint>} |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [delete コマンド](delete.md)
