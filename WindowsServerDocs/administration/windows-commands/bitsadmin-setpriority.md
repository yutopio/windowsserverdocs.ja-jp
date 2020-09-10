---
title: bitsadmin setpriority
description: 指定されたジョブの優先度を設定する bitsadmin setpriority コマンドの参照記事です。
ms.topic: reference
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 25bf7026ceef21fb37824ce99f56389941426b79
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630724"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority

指定されたジョブの優先順位を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setpriority <job> <priority>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| priority | ジョブの優先順位を設定します。次に例を示します。<ul><li>FOREGROUND</li><li>HIGH</li><li>NORMAL</li><li>LOW</li></ul> |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの優先順位を normal に設定するには、次のようにします。

```
bitsadmin /setpriority myDownloadJob NORMAL
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
