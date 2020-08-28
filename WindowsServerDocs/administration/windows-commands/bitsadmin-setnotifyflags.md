---
title: bitsadmin setnotifyflags
description: Bitsadmin setnotifyflags コマンドの参照記事。指定されたジョブのイベント通知フラグを設定します。
ms.topic: reference
ms.assetid: d5763d95-94a6-45ca-9e03-891c20047e06
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: a3b00d057659b2664098093c0a7e3b13b28cd806
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026220"
---
# <a name="bitsadmin-setnotifyflags"></a>bitsadmin setnotifyflags

指定されたジョブのイベント通知フラグを設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setnotifyflags <job> <notifyflags>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
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
