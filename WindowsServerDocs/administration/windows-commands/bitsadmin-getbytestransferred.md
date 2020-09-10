---
title: bitsadmin getbytestransferred
description: Bitsadmin getbytestransferred コマンドの参照記事。指定されたジョブで転送されたバイト数を取得します。
ms.topic: reference
ms.assetid: 47bbf184-e06f-4be0-b2ba-d32b10d82002
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c67185ff147611436dcb75803e2282542f376019
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632301"
---
# <a name="bitsadmin-getbytestransferred"></a>bitsadmin getbytestransferred

指定したジョブに対して転送されたバイト数を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getbytestransferred <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブで転送されたバイト数を取得するには、次のようにします。

```
bitsadmin /getbytestransferred myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
