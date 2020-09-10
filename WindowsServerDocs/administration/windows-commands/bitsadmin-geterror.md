---
title: bitsadmin geterror
description: Bitsadmin geterror コマンドの参照記事。指定されたジョブの詳細なエラー情報を取得します。
ms.topic: reference
ms.assetid: cbe5bca1-d2dd-4ce6-903f-f85de4a2ec6a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1cfa4c5a7d0899e2d5eb34fd089944f2b801993a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632121"
---
# <a name="bitsadmin-geterror"></a>bitsadmin geterror

指定されたジョブの詳細なエラー情報を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /geterror <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのエラー情報を取得するには、次のようにします。

```
bitsadmin /geterror myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
