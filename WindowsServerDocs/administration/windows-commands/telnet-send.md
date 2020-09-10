---
title: telnet send
description: Telnet サーバーに telnet コマンドを送信する telnet 送信の参照記事。
ms.topic: reference
ms.assetid: 7c217abc-1182-466e-914c-1ff16755021b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: bef40b0015ccfdc5c62b6acc8b42bc95865ca0ff
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639818"
---
# <a name="telnet-send"></a>telnet: 送信

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Telnet サーバーに telnet コマンドを送信します。

## <a name="syntax"></a>構文
```
sen[d] {ao | ayt | brk | esc | ip | synch | <string>} [?]
```
#### <a name="parameters"></a>パラメーター

| パラメーター |                     説明                      |
|-----------|------------------------------------------------------|
|    ao     |       Telnet コマンドの中止出力を送信します。        |
|    ayt    |       Telnet コマンドを送信します。       |
|    brk    |            Telnet コマンド brk を送信します。            |
|    esc    |      現在の telnet エスケープ文字を送信します。      |
|    ip     |     Telnet コマンドの割り込みプロセスを送信します。     |
|   同期   |           Telnet コマンド同期を送信します。           |
| <string>  | 入力した任意の文字列を telnet サーバーに送信します。 |
|     ?     |     このコマンドに関連するヘルプを表示します。      |

## <a name="examples"></a>例
Telnet サーバーに送信されます。
```
sen ayt
```
## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)
