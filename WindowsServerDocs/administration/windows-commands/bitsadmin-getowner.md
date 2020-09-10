---
title: bitsadmin getowner
description: Bitsadmin getowner コマンドの参照記事。指定されたジョブの所有者を取得します。
ms.topic: reference
ms.assetid: 5203f84c-a879-4f31-ae3e-7ea74bd63ca5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2839936113e304e9c57308042f5c8cf66e887d36
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631873"
---
# <a name="bitsadmin-getowner"></a>bitsadmin getowner

指定したジョブの所有者の表示名または GUID が表示されます。

## <a name="syntax"></a>構文

```
bitsadmin /getowner <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの所有者を表示するには、次のようにします。

```
bitsadmin /getowner myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
