---
title: bitsadmin gettemporaryname
description: Bitsadmin gettemporary name コマンドの参照記事。ジョブ内の指定されたファイルの一時ファイル名を報告します。
ms.topic: reference
ms.assetid: 68925edc-a801-4292-a812-7471c4f60fdd
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9eeaf3c1093cf147c945bb029e5652db1819003c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631594"
---
# <a name="bitsadmin-gettemporaryname"></a>bitsadmin gettemporaryname

ジョブ内の指定されたファイルの一時ファイル名を報告します。

## <a name="syntax"></a>構文

```
bitsadmin /gettemporaryname <job> <file_index>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| file_index | 0から開始します。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのファイル2の一時ファイル名を報告するには、次のようにします。

```
bitsadmin /gettemporaryname myDownloadJob 1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
