---
title: bitsadmin setmaxdownloadtime
description: ダウンロードタイムアウトを秒単位で設定する bitsadmin setmaxdownloadtime コマンドの参照記事。
ms.topic: reference
ms.assetid: 16b96cf1-5738-415c-9b9d-c4ea8d5e4fec
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a4b0096aeb14c4c8cb69654ad4b3723977d759ef
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024255"
---
# <a name="bitsadmin-setmaxdownloadtime"></a>bitsadmin setmaxdownloadtime

ダウンロードタイムアウトを秒単位で設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setmaxdownloadtime <job> <timeout>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| timeout | ダウンロードタイムアウトの長さ (秒単位)。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのタイムアウトを10秒に設定します。

```
bitsadmin /setmaxdownloadtime myDownloadJob 10
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
