---
title: ftp remotehelp
description: リモートコマンドのヘルプを表示する、ftp remotehelp コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: ef23adf3-ead4-44c8-ac1d-c8a6f4b2bf73
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c91fda83ea988f79237b27f6df6bd6062748e37c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639377"
---
# <a name="ftp-remotehelp"></a>ftp remotehelp

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートコマンドのヘルプを表示します。

## <a name="syntax"></a>構文

```
remotehelp [<command>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| `[<command>]` | ヘルプを表示するコマンドの名前を指定します。 が `<command>` 指定されていない場合、このコマンドはすべてのリモートコマンドの一覧を表示します。 また、 [ftp 引用符](ftp-quote.md) または [ftp リテラル](ftp-literal_1.md)を使用してリモートコマンドを実行することもできます。 |

### <a name="examples"></a>例

リモートコマンドの一覧を表示するには、次のように入力します。

```
remotehelp
```

この *コマンドの構文* を表示するには、次のように入力します。

```
remotehelp feat
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ftp quote](ftp-quote.md)

- [ftp literal](ftp-literal_1.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
