---
title: bitsadmin getcreationtime
description: Bitsadmin get time コマンドの参照記事。指定されたジョブの作成時刻を取得します。
ms.topic: reference
ms.assetid: be409cb5-ce72-41d9-aafa-edd4e230fd14
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1175b148e0169f5b8f76d66ae3358a1069f5c4f7
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030430"
---
# <a name="bitsadmin-getcreationtime"></a>bitsadmin getcreationtime

指定されたジョブの作成時刻を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getcreationtime <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの作成時刻を取得するには、次のようにします。

```
bitsadmin /getcreationtime myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
