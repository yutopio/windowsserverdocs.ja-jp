---
title: bitsadmin getpriority
description: Bitsadmin getpriority コマンドの参照記事。指定されたジョブの優先順位を取得します。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 2aeff973b0ca285cc8c9852f284e314879f8de02
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028700"
---
# <a name="bitsadmin-getpriority"></a>bitsadmin getpriority

指定されたジョブの優先順位を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getpriority <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

#### <a name="output"></a>Output

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
