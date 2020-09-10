---
title: bitsadmin info
description: Bitsadmin info コマンドの参照記事。指定されたジョブに関する概要情報が表示されます。
ms.topic: reference
ms.assetid: 5c306677-0d64-41c0-8276-5bba7750cecb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 815fdc719d584f7d25f88705056e4d5c0c3405aa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631530"
---
# <a name="bitsadmin-info"></a>bitsadmin info

指定されたジョブに関する概要情報を表示します。

## <a name="syntax"></a>構文

```
bitsadmin /info <job> [/verbose]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| /verbose | 省略可能。 各ジョブの詳細情報を提供します。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブに関する情報を取得するには、次のようにします。

```
bitsadmin /info myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin info](bitsadmin-info.md)
