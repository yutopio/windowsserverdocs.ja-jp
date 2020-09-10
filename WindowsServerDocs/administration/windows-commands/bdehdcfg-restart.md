---
title: bdehdcfg restart
description: Bdehdcfg restart コマンドのリファレンス記事。ドライブの準備が完了した後で、コンピューターを再起動する必要があることを bdehdcfg に伝えます。
ms.topic: reference
ms.assetid: a98b76bb-36f1-4790-b337-7dc35f606bc6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0839f22bed8dee63fb25f9b254e36b0c02c88399
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632830"
---
# <a name="bdehdcfg-restart"></a>bdehdcfg: 再起動

ドライブの準備が完了した後にコンピューターを再起動する必要があることを bdehdcfg コマンドラインツールに通知します。 他のユーザーがコンピューターにログオンしていて、 **quiet** コマンドが指定されていない場合は、コンピューターを再起動するかどうかを確認するメッセージが表示されます。

## <a name="syntax"></a>構文

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -restart
```

#### <a name="parameters"></a>パラメーター

このコマンドには追加のパラメーターはありません。

## <a name="examples"></a>例

**Restart**コマンドを使用するには:

```
bdehdcfg -target default -restart
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
