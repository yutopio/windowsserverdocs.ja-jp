---
title: bitsadmin getminretrydelay
description: Bitsadmin getminretrydelay コマンドの参照記事。このコマンドは、ファイルの転送を試行する前に、サービスが一時的なエラーを検出した後に待機する時間 (秒単位) を取得します。
ms.topic: reference
ms.assetid: 54f0abab-c129-40ed-a603-50f464d26011
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: be71dc355e966b4a6ac627045f1ec5ceaf68f2d3
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631944"
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
