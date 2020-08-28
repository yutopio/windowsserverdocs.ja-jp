---
title: bitsadmin getreplyfilename
description: Bitsadmin getreplyfilename コマンドの参照記事。このコマンドは、ジョブのサーバーアップロード応答を含むファイルのパスを取得します。
ms.topic: reference
ms.assetid: 85447184-1732-4816-a365-2e3599551bf8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3c2e355bf0264c5dc995f0d241afe7b641d2a41b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034880"
---
# <a name="bitsadmin-getreplyfilename"></a>bitsadmin getreplyfilename

ジョブのサーバーアップロード-応答を含むファイルのパスを取得します。

> [!NOTE]
> このコマンドは、BITS 1.2 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /getreplyfilename <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのアップロード応答ファイル名を取得するには、次のようにします。

```
bitsadmin /getreplyfilename myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
