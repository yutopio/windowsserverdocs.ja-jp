---
title: bitsadmin cache および setexpirationtime
description: キャッシュの有効期限を設定する bitsadmin cache と setexpirationtime コマンドの参照記事。
ms.topic: reference
ms.assetid: 00ea6e4e-b707-4b31-88dd-b61a78565c8d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e07e862d8577c33daec24bbc93fe5859f13944db
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028810"
---
# <a name="bitsadmin-cache-and-setexpirationtime"></a>bitsadmin cache および setexpirationtime

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

キャッシュの有効期限を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /cache /setexpirationtime secs
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
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
