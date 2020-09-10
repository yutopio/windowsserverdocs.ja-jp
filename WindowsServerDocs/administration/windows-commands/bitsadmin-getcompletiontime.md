---
title: bitsadmin getcompletiontime
description: Bitsadmin get time コマンドの参照記事。これは、ジョブがデータの転送を終了した時刻を取得します。
ms.topic: reference
ms.assetid: 7a4b3c1c-9832-4724-86b2-cce3c01bfa28
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 660a28dcfe99bd5801ba2fc3ad909cec78a671ce
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632247"
---
# <a name="bitsadmin-getcompletiontime"></a>bitsadmin getcompletiontime

ジョブがデータの転送を終了した時刻を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getcompletiontime <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブがデータの転送を終了した時刻を取得するには、次の操作を行います。

```
bitsadmin /getcompletiontime myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
