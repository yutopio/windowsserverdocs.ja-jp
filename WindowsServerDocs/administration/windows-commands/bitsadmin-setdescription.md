---
title: bitsadmin setdescription
description: Bitsadmin setdescription コマンドの参照記事。指定されたジョブの説明を設定します。
ms.topic: reference
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 86f63a553b9d308ef3e8bfe5bfc2a2334b5d28e8
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031260"
---
# <a name="bitsadmin-setdescription"></a>bitsadmin setdescription

指定されたジョブの説明を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setdescription <job> <description>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| description | ジョブを説明するために使用されるテキストです。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの説明を取得するには、次のようにします。

```
bitsadmin /setdescription myDownloadJob music_downloads
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
