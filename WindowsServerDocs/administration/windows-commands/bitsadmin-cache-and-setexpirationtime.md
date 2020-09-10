---
title: bitsadmin cache および setexpirationtime
description: キャッシュの有効期限を設定する bitsadmin cache と setexpirationtime コマンドの参照記事。
ms.topic: reference
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0d9bc67292796afdbcec695ea2e65966b5b5e46d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632529"
---
# <a name="bitsadmin-cache-and-setexpirationtime"></a>bitsadmin cache および setexpirationtime

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

キャッシュの有効期限を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /cache /setexpirationtime secs
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| 秒数 | キャッシュの有効期限が切れるまでの秒数。 |

## <a name="examples"></a>例

キャッシュの有効期限を60秒で設定するには、次のようにします。

```
bitsadmin /cache / setexpirationtime 60
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin cache コマンド](bitsadmin-cache.md)
