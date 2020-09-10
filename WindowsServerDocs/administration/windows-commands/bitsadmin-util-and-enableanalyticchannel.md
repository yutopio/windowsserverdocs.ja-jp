---
title: bitsadmin util および enableanalyticchannel
description: BITS クライアント分析チャネルを有効または無効にする bitsadmin util および enableanalytics のチャネルコマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 0d7645aa-b91b-4ed7-b630-a1e1be6f6ae9
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 391b53694fcb21d1c17085d487908b090ad88f0a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630566"
---
# <a name="bitsadmin-util-and-enableanalyticchannel"></a>bitsadmin util および enableanalyticchannel

BITS クライアント分析チャネルを有効または無効にします。

## <a name="syntax"></a>Syntax

```
bitsadmin /util /enableanalyticchannel TRUE|FALSE
```

| パラメーター | Description |
| --------- | ---------- |
| TRUE または FALSE | **TRUE** を指定すると、指定したファイルのコンテンツの検証が有効になり、 **FALSE** の場合は無効になります。 |

## <a name="examples"></a>例

BITS クライアントの分析チャネルをオンまたはオフにします。

```
bitsadmin /util / enableanalyticchannel TRUE
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin util コマンド](bitsadmin-util.md)

- [bitsadmin コマンド](bitsadmin.md)
