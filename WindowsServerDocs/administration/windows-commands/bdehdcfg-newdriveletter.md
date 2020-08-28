---
title: bdehdcfg newdriveletter
description: Bdehdcfg newdriveletter コマンドの参照記事。システムドライブとして使用されるドライブの部分に新しいドライブ文字を割り当てます。
ms.topic: reference
ms.assetid: f1f200a0-6850-4f0d-9047-f9f982a590f8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cf3cf52bfd23db5aadd82170de2bf20c8e602573
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031550"
---
# <a name="bdehdcfg-newdriveletter"></a>bdehdcfg: newdriveletter

システムドライブとして使用されるドライブの部分に新しいドライブ文字を割り当てます。 ベストプラクティスとして、システムドライブにドライブ文字を割り当てないことをお勧めします。

## <a name="syntax"></a>構文

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -newdriveletter <drive_letter>
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---------| ----------- |
| `<drive_letter>` | 指定されたターゲットドライブに割り当てられるドライブ文字を定義します。 |

## <a name="examples"></a>例

ドライブ文字を既定のドライブに割り当てるには、次のようにし `P` ます。

```
bdehdcfg -target default -newdriveletter P:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
