---
title: bitsadmin gethelpertokensid
description: BITS 転送ジョブのヘルパートークンが設定されている場合、その SID を返す bitsadmin geの pertokensid コマンドの参照記事。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 645957ab5526c98e806a4e7875e1baece3d375b3
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632041"
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

| パラメーター | Description |
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
