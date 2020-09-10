---
title: bitsadmin setnotifyflags
description: Bitsadmin setnotifyflags コマンドの参照記事。指定されたジョブのイベント通知フラグを設定します。
ms.topic: reference
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 48eb165ecb32e53868f9636418437d66c56542c0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630773"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

指定されたジョブのイベント通知フラグを設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setnotifyflags <job> <notifyflags>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| notifyflags | には、次のような通知フラグを1つ以上含めることができます。<ul><li>1. ジョブ内のすべてのファイルが転送されたときにイベントを生成**します。**</li><li>2. エラーが発生したときにイベントを生成**します。**</li><li>3. すべてのファイルの転送が完了したとき、またはエラーが発生したときに、イベントを生成**します。**</li><li>**4.** 通知を無効にします。</li></ul> |

## <a name="examples"></a>例

エラーが発生したときにイベントを生成するように通知フラグを設定するには、 *Mydownloadjob*という名前のジョブを使用します。

```
bitsadmin /setnotifyflags myDownloadJob 2
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
