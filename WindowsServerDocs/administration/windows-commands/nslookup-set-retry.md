---
title: nslookup set retry
description: Nslookup set retry コマンドの参照記事。指定されたサーバーから情報を取得する試行回数を設定します。
ms.topic: reference
ms.assetid: 615fdfa2-fa29-47a8-8c9e-a6c5b45b3b71
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: fa8b588c49b61c2269325b1b9e67d350f837c5ad
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637525"
---
# <a name="nslookup-set-retry"></a>nslookup set retry

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

一定の時間内に応答が受信されなかった場合、タイムアウト期間は2倍になり、要求は再送信されます。 このコマンドは、要求がサーバーに再送信されてから情報が得られるまでの回数を設定します。

> [!NOTE]
> 要求がタイムアウトになるまでの時間を変更するには、 [nslookup set timeout](nslookup-set-timeout.md) コマンドを使用します。

## <a name="syntax"></a>構文

```
set retry=<number>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---------- | ---------- |
| `<number>` | 再試行回数の新しい値を指定します。 既定の再試行回数は **4**です。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [nslookup set timeout](nslookup-set-timeout.md)
