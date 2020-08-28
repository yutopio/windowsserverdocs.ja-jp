---
title: bitsadmin getminretrydelay
description: Bitsadmin getminretrydelay コマンドの参照記事。このコマンドは、ファイルの転送を試行する前に、サービスが一時的なエラーを検出した後に待機する時間 (秒単位) を取得します。
ms.topic: reference
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1f5bc6d69e7dbc46bc7e0df3a34ac97f37fda252
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030310"
---
# <a name="bitsadmin-getminretrydelay"></a>bitsadmin getminretrydelay

ファイルの転送を試行する前に、サービスが一時的なエラーを検出した後に待機する時間 (秒単位) を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getminretrydelay <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの最小再試行間隔を取得するには、次のようにします。

```
bitsadmin /getminretrydelay myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
