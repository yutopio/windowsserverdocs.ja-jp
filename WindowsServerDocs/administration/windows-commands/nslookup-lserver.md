---
title: nslookup lserver
description: Nslookup lserver コマンドの参照記事。最初のサーバーを指定したドメインネームシステム (DNS) ドメインに変更します。
ms.topic: reference
ms.assetid: aee5ea0b-bb17-4c14-bde7-2f7a91f2f22b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d1f507b1a61e9fd4fc506fb4e74f869c83e95335
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635670"
---
# <a name="nslookup-lserver"></a>nslookup lserver

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定したドメインネームシステム (DNS) ドメインに初期サーバーを変更します。

このコマンドは、初期サーバーを使用して、指定された DSN ドメインに関する情報を検索します。 現在の既定のサーバーを使用して情報を参照する場合は、 [nslookup server](nslookup-server.md) コマンドを使用します。

## <a name="syntax"></a>構文

```
lserver <DNSdomain>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<DNSdomain>` | 初期サーバーの DNS ドメインを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [nslookup server](nslookup-server.md)
