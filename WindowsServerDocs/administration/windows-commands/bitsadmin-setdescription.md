---
title: bitsadmin setdescription
description: Bitsadmin setdescription コマンドの参照記事。指定されたジョブの説明を設定します。
ms.topic: reference
ms.assetid: 1e46a5dd-4637-4a2e-b88f-d3f85b177db8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a306605d447a3bc3a40b16f75a1a63badf75f3b0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630941"
---
# <a name="bitsadmin-setdescription"></a>bitsadmin setdescription

指定されたジョブの説明を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setdescription <job> <description>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
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
