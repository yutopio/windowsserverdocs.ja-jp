---
title: nslookup server
description: Nslookup サーバーコマンドの参照記事。既定のサーバーを指定したドメインネームシステム (DNS) ドメインに変更します。
ms.topic: reference
ms.assetid: 608267f8-f7b4-412a-8dcd-e08b5ffc2085
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 32450197fe7d3c04258b7fb3f77f8e17cd1c113e
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038763"
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
