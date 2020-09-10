---
title: bitsadmin listfiles
description: 指定されたジョブ内のファイルを一覧表示する bitsadmin listfiles コマンドの参照記事です。
ms.topic: reference
ms.assetid: ad0d1eaa-3bd8-45e5-8f72-4da7366f0d59
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 702c2d3d3370275373a91aef63aa82f7e84bcf14
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631509"
---
# <a name="bitsadmin-listfiles"></a>bitsadmin listfiles

指定されたジョブ内のファイルを一覧表示します。

## <a name="syntax"></a>構文

```
bitsadmin /listfiles <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのファイルの一覧を取得するには、次のようにします。

```
bitsadmin /listfiles myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
