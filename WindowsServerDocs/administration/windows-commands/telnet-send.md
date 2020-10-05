---
title: telnet send
description: Telnet サーバーに telnet コマンドを送信する telnet 送信コマンドの参照記事です。
ms.topic: reference
ms.assetid: 7c217abc-1182-466e-914c-1ff16755021b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ab6c94f619ab28be7b850479a7e3d476e1394e09
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91717989"
---
# <a name="telnet-send"></a>telnet: 送信

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Telnet サーバーに telnet コマンドを送信します。

## <a name="syntax"></a>構文

```
sen {ao | ayt | brk | esc | ip | synch | <string>} [?]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| ao | Telnet コマンドの **中止出力**を送信します。 |
| ayt | Telnet コマンドを送信し **ますか。** |
| brk | Telnet コマンド **brk**を送信します。 |
| esc | 現在の telnet エスケープ文字を送信します。 |
| ip | Telnet コマンドの **割り込みプロセス**を送信します。 |
| 同期 | Telnet コマンド同期を送信します。 |
| `<string>` | 入力した任意の文字列を telnet サーバーに送信します。 |
| ? | このコマンドに関連するヘルプを表示します。 |

## <a name="example"></a>例

Telnet サーバーにコマンドを送信するに **は** 、次のように入力します。

```
sen ayt
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
