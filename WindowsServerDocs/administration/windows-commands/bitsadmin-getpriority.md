---
title: bitsadmin getpriority
description: Bitsadmin getpriority コマンドの参照記事。指定されたジョブの優先順位を取得します。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 397a762a210aeae7a02e49283330a2d4214876e6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631761"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin getpriority

指定されたジョブの優先順位を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getpriority <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

#### <a name="output"></a>出力

このコマンドで返される優先順位は次のとおりです。

- **フォア**

- **高い**

- **通常**

- **低画質**

- **UNKNOWN**

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの優先順位を取得するには、次のようにします。

```
bitsadmin /getpriority myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
