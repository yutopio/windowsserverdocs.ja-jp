---
title: bitsadmin cancel
description: Bitsadmin cancel コマンドの参照記事。転送キューからジョブを削除し、ジョブに関連付けられているすべての一時ファイルを削除します。
ms.topic: reference
ms.assetid: 7374b544-6a16-4d3e-872c-dcf4c02ad89d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: da7a858603875affc7acc8bcb60d02451a641690
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024436"
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
