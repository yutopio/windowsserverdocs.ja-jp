---
title: bdehdcfg quiet
description: Bdehdcfg quiet コマンドのリファレンス記事。すべてのアクションとエラーを表示しないように bdehdcfg に指示します。
ms.topic: reference
ms.assetid: 7f75b702-890b-4ff9-805c-edf5cadd8822
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 463dd8d558c4704f0997e867af73c5775c3b9f07
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632874"
---
# <a name="bdehdcfg-quiet"></a>bdehdcfg: quiet

Bdehdcfg コマンドラインツールに、すべてのアクションとエラーがコマンドラインインターフェイスに表示されないことを通知します。 ドライブの準備中に表示される [はい/いいえ] (Y/N) プロンプトでは、"Yes" という答えが想定されます。 ドライブの準備中に発生したエラーを表示するには、 **DrivePreparationTool** イベントプロバイダーの下にあるシステムイベントログを確認します。

## <a name="syntax"></a>構文

```
bdehdcfg -target {default|unallocated|<drive_letter> shrink|<drive_letter> merge} -quiet
```

#### <a name="parameters"></a>パラメーター

このコマンドには追加のパラメーターはありません。

## <a name="examples"></a>例

**Quiet**コマンドを使用するには、次のようにします。

```
bdehdcfg -target default -quiet
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bdehdcfg](bdehdcfg.md)
