---
title: nslookup server
description: Nslookup サーバーコマンドの参照記事。既定のサーバーを指定したドメインネームシステム (DNS) ドメインに変更します。
ms.topic: reference
ms.assetid: 608267f8-f7b4-412a-8dcd-e08b5ffc2085
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 64d1383dd5c4fa86a62fad91bae0ed5e4eb1454b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635619"
---
# <a name="nslookup-server"></a>nslookup server

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定したドメインネームシステム (DNS) ドメインに既定のサーバーを変更します。

このコマンドは、現在の既定のサーバーを使用して、指定された DSN ドメインに関する情報を検索します。 最初のサーバーを使用して情報を参照する場合は、 [nslookup lserver](nslookup-lserver.md) コマンドを使用します。

## <a name="syntax"></a>構文

```
server <DNSdomain>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<DNSdomain>` | 既定のサーバーの DNS ドメインを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [nslookup lserver](nslookup-lserver.md)
