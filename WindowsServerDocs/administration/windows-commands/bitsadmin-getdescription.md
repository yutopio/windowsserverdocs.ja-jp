---
title: bitsadmin getdescription
description: Bitsadmin getdescription コマンドの参照記事。指定されたジョブの説明を取得します。
ms.topic: reference
ms.assetid: f3974603-ebbe-4d31-8217-040fe2d90c85
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ddc3ef5f5f8328182e91ed7ae3026e94464267b7
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632146"
---
# <a name="bitsadmin-getdescription"></a>bitsadmin getdescription

指定されたジョブの説明を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getdescription <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの説明を取得するには、次のようにします。

```
bitsadmin /getdescription myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
