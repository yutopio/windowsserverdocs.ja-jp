---
title: bitsadmin setdisplayname
description: Bitsadmin setdisplayname コマンドの参照記事。指定されたジョブの表示名を設定します。
ms.topic: reference
ms.assetid: 13706c53-fb5f-4879-b5ca-82531361d6e1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 57a72d198b7d262f3a7958920e5d54955f8b6270
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630934"
---
# <a name="bitsadmin-setdisplayname"></a>bitsadmin setdisplayname

指定されたジョブの表示名を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setdisplayname <job> <display_name>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| display_name | 特定のジョブの表示名として使用されるテキスト。 |

## <a name="examples"></a>例

ジョブの表示名を *Mydownloadjob*に設定するには、次のようにします。

```
bitsadmin /setdisplayname myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
