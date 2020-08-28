---
title: bitsadmin getreplydata
description: Bitsadmin getreplydata コマンドの参照記事。このコマンドは、サーバーのアップロード/応答データをジョブの16進形式で取得します。
ms.topic: reference
ms.assetid: 819f97d5-b255-4b2d-9f63-0daa73915434
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4e00a17e4633c9b065d03684cb0c953d1f6db811
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031340"
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

| パラメーター | 説明 |
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
