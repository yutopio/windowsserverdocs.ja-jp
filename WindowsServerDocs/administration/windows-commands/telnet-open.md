---
title: telnet open
description: Telnet サーバーに接続する telnet open コマンドのリファレンス記事です。
s.topic: article
ms.assetid: e30ad68c-2366-4754-ac36-311a2392902a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6db7f428f4b8c85c6e953a8fe4a9328b965898f8
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718009"
---
# <a name="telnet-open"></a>telnet: 開く

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Telnet サーバーに接続します。

## <a name="syntax"></a>構文

```
o[pen] <hostname> [<port>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<hostname>` | コンピューター名または IP アドレスを指定します。 |
| `[<port>]` | Telnet サーバーがリッスンしている TCP ポートを指定します。 既定値は、TCP ポート 23 です。 |

## <a name="examples"></a>例

*Telnet.microsoft.com*で telnet サーバーに接続するには、次のように入力します。

```
o telnet.microsoft.com
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
