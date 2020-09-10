---
title: bitsadmin setmaxdownloadtime
description: ダウンロードタイムアウトを秒単位で設定する bitsadmin setmaxdownloadtime コマンドの参照記事。
ms.topic: reference
ms.assetid: 16b96cf1-5738-415c-9b9d-c4ea8d5e4fec
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9937a4f2945e45d351cfa3506a9aefbd4723f37c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630814"
---
# <a name="bitsadmin-setmaxdownloadtime"></a>bitsadmin setmaxdownloadtime

ダウンロードタイムアウトを秒単位で設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setmaxdownloadtime <job> <timeout>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
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
