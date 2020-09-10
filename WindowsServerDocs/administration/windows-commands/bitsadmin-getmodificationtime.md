---
title: bitsadmin getmodificationtime
description: Bitsadmin getmodificationtime コマンドの参照記事。ジョブが最後に変更された時刻、またはデータが正常に転送された日時を取得します。
ms.topic: reference
ms.assetid: e543945e-92c4-491e-8c2d-344f8a3e342d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 293b8ef47374c0df3f9b1cd3d76802d592c3c522
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631931"
---
# <a name="bitsadmin-getmodificationtime"></a>bitsadmin getmodificationtime

ジョブが最後に変更された時刻、またはデータが正常に転送された日時を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getmodificationtime <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの最終更新時刻を取得するには、次のようにします。

```
bitsadmin /getmodificationtime myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
