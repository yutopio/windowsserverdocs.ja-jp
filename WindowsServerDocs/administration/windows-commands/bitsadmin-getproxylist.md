---
title: bitsadmin getproxylist-指定したジョブのプロキシの一覧を取得します。
description: 指定されたジョブのプロキシ一覧を取得する bitsadmin getproxylist コマンドの参照記事です。
ms.topic: reference
ms.assetid: eebfa727-d8f1-4ae3-9382-6d8ffe8c3df3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4d4cefcb27a9aa18b06bc588d08aba2f2f810636
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631748"
---
# <a name="bitsadmin-getproxylist"></a>bitsadmin getproxylist

指定したジョブに使用するプロキシサーバーのコンマ区切りの一覧を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getproxylist <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのプロキシ一覧を取得するには、次のようにします。

```
bitsadmin /getproxylist myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
