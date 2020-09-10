---
title: nslookup set timeout
description: Nslookup set timeout コマンドの参照記事。これにより、検索要求への応答を待機する秒数の初期値が変更されます。
ms.topic: reference
ms.assetid: 07afdaf4-ffec-496f-a188-4e91cf1a28f8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b470598378f1b338da209ea16a0d8102177c573c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640529"
---
# <a name="nslookup-set-timeout"></a>nslookup set timeout

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

検索要求への応答を待機する秒数の初期値を変更します。 指定した時間内に応答が受信されなかった場合、タイムアウト期間は2倍になり、要求は再送信されます。 [Nslookup set retry](nslookup-set-retry.md)コマンドを使用して、要求の送信を試行する回数を決定します。

## <a name="syntax"></a>構文

```
set timeout=<number>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---------- | ---------- |
| `<number>` | 応答を待機する秒数を指定します。 待機する既定の秒数は **5**です。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

応答の取得のタイムアウトを2秒に設定するには、次のようにします。

```
set timeout=2
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [nslookup set retry](nslookup-set-retry.md)
