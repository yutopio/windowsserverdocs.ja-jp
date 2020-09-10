---
title: bitsadmin getreplydata
description: Bitsadmin getreplydata コマンドの参照記事。このコマンドは、サーバーのアップロード/応答データをジョブの16進形式で取得します。
ms.topic: reference
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a15dc59d9487ed928954f8d5cbd47828c2b58291
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631719"
---
# <a name="bitsadmin-getreplydata"></a>bitsadmin getreplydata

サーバーのアップロード応答データを、ジョブの16進形式で取得します。

> [!NOTE]
> このコマンドは、BITS 1.2 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /getreplydata <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのアップロード応答データを取得するには、次のようにします。

```
bitsadmin /getreplydata myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
