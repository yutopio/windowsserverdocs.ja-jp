---
title: bitsadmin gettype
description: Bitsadmin gettype コマンドの参照記事。指定されたジョブのジョブの種類を取得します。
ms.topic: reference
ms.assetid: bec16f04-3e95-4587-889e-3de6ad03c9c8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ccb938e1fe67164567bbe8d6c87d87423026db96
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631565"
---
# <a name="bitsadmin-gettype"></a>bitsadmin gettype

指定されたジョブの種類を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /gettype <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

#### <a name="output"></a>出力

返される出力値は次のようになります。

| 型 | 説明 |
| --------------- | ----------- |
| ダウンロード | このジョブはダウンロードです。 |
| アップロード | ジョブはアップロードです。 |
| アップロード-応答 | ジョブは、アップロード応答です。 |
| Unknown | ジョブの種類が不明です。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのジョブの種類を取得するには、次のようにします。

```
bitsadmin /gettype myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
