---
title: bdehdcfg size
description: 新しいシステムドライブを作成するときのシステムパーティションのサイズを指定する、bdehdcfg size コマンドの参照記事です。
ms.topic: reference
ms.assetid: 80f55b1d-a28d-4edf-9997-1fb918b7b5a1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: f4aaedbbac5783fdf54814d7cf97ef9c70c9d346
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031480"
---
# <a name="bdehdcfg-size"></a>bdehdcfg: サイズ

新しいシステムドライブを作成するときのシステムパーティションのサイズを指定します。 サイズを指定しない場合、ツールでは既定値の 300 MB が使用されます。 システムドライブの最小サイズは 100 MB です。 システムの回復などのシステムツールをシステムパーティションに格納する場合は、それに応じてサイズを大きくする必要があります。

> [!NOTE]
> **Size**コマンドをコマンドと組み合わせて使用することはできません `target <drive_letter> merge` 。

## <a name="syntax"></a>構文

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink} -size <size_in_mb>
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<size_in_mb>` | 新しいパーティションに使用するメガバイト (MB) 数を示します。 |

## <a name="examples"></a>例

既定のシステムドライブに 500 MB を割り当てるには、次のようにします。

```
bdehdcfg -target default -size 500
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
