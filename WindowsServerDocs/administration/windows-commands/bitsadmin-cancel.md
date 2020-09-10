---
title: bitsadmin cancel
description: Bitsadmin cancel コマンドの参照記事。転送キューからジョブを削除し、ジョブに関連付けられているすべての一時ファイルを削除します。
ms.topic: reference
ms.assetid: 7374b544-6a16-4d3e-872c-dcf4c02ad89d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4ef8810b04141b41851f029f6cde4586b89a90d4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632423"
---
# <a name="bitsadmin-cancel"></a>bitsadmin cancel

転送キューからジョブを削除し、ジョブに関連付けられているすべての一時ファイルを削除します。

## <a name="syntax"></a>構文

```
bitsadmin /cancel <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

転送キューから *Mydownloadjob* ジョブを削除するには、次のようにします。

```
bitsadmin /cancel myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
