---
title: bitsadmin getnotifycmdline
description: Bitsadmin getnotifycmdline コマンドの参照記事。ジョブがデータの転送を終了したときに実行されるコマンドラインコマンドを取得します。
ms.topic: reference
ms.assetid: 90fa33e6-aca5-4a23-82bd-19a9f13f8416
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d85ed3dc301aed9d79619a1bbc6e9dc835b2102a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033480"
---
# <a name="bitsadmin-getnotifycmdline"></a>bitsadmin getnotifycmdline

指定されたジョブがデータの転送を終了した後に実行するコマンドラインコマンドを取得します。

> [!NOTE]
> このコマンドは、BITS 1.2 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /getnotifycmdline <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブが完了したときにサービスによって使用されるコマンドラインコマンドを取得すること。

```
bitsadmin /getnotifycmdline myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
