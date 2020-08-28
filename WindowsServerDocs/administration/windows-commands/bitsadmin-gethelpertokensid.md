---
title: bitsadmin gethelpertokensid
description: BITS 転送ジョブのヘルパートークンが設定されている場合、その SID を返す bitsadmin geの pertokensid コマンドの参照記事。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 9cfa2c2a10d1f3947374262bbeb9ab21e559cfee
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033550"
---
# <a name="bitsadmin-gethelpertokensid"></a>bitsadmin gethelpertokensid

BITS 転送ジョブの [ヘルパートークン](/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)が設定されている場合、その SID を返します。

> [!NOTE]
> このコマンドは、BITS 3.0 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /gethelpertokensid <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前の BITS 転送ジョブの SID を取得するには、次のようにします。

```
bitsadmin /gethelpertokensid myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
