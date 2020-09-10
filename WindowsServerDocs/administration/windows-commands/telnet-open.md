---
title: telnet open
description: Telnet サーバーに接続する telnet open の参照記事です。
s.topic: article
ms.assetid: e30ad68c-2366-4754-ac36-311a2392902a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 892d797c4b56acb46e8119237fd38296e4ae411c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636788"
---
# <a name="telnet-open"></a>telnet: 開く

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Telnet サーバーに接続します。

## <a name="syntax"></a>構文
```
o[pen] <hostname> [<Port>]
```
#### <a name="parameters"></a>パラメーター

| パラメーター  |                                        説明                                         |
|------------|--------------------------------------------------------------------------------------------|
| <hostname> |                         コンピューター名または IP アドレスを指定します。                         |
|  [<Port>]  | Telnet サーバーがリッスンしている TCP ポートを指定します。 既定値は、TCP ポート 23 です。 |

## <a name="examples"></a>例
Telnet.microsoft.com で telnet サーバーに接続します。
```
o telnet.microsoft.com
```
## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)
