---
title: bitsadmin getbytestransferred
description: Bitsadmin getbytestransferred コマンドの参照記事。指定されたジョブで転送されたバイト数を取得します。
ms.topic: reference
ms.assetid: 47bbf184-e06f-4be0-b2ba-d32b10d82002
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 67e1432f2fbef32ac47320d87993f5d62053bb71
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028740"
---
# <a name="bitsadmin-getbytestransferred"></a>bitsadmin getbytestransferred

指定したジョブに対して転送されたバイト数を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getbytestransferred <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
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
