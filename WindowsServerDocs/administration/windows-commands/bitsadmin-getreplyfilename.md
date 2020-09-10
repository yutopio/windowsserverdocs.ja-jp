---
title: bitsadmin getreplyfilename
description: Bitsadmin getreplyfilename コマンドの参照記事。このコマンドは、ジョブのサーバーアップロード応答を含むファイルのパスを取得します。
ms.topic: reference
ms.assetid: 85447184-1732-4816-a365-2e3599551bf8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d3dab8e7f2a50c00c1c5ccb72f4e6dea76df3090
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631709"
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

| パラメーター | Description |
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
