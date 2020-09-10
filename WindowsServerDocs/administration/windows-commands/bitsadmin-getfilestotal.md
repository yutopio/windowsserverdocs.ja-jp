---
title: bitsadmin getfilestotal
description: Bitsadmin getfilestotal コマンドの参照記事。指定されたジョブ内のファイルの数を取得します。
ms.topic: reference
ms.assetid: c5de113e-f29c-4cd3-9392-0e300018d516
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 73a543914f31a7b9e5b028caf273d7945a954fdd
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632106"
---
# <a name="bitsadmin-getfilestotal"></a>bitsadmin getfilestotal

指定されたジョブ内のファイルの数を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getfilestotal <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブに含まれるファイルの数を取得するには、次のようにします。

```
bitsadmin /getfilestotal myDownloadJob
```

## <a name="see-also"></a>参照

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
