---
title: bitsadmin getpeercachingflags
description: Bitsadmin getpeercachingflags コマンドの参照記事。ジョブのファイルをキャッシュしてピアに提供できるかどうか、および BITS がピアからジョブのコンテンツをダウンロードできるかどうかを決定するフラグを取得します。
ms.topic: reference
ms.assetid: 3c3c9f28-4c04-4c49-a23a-dee5bbcc8981
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6ec765183543bf42152d198c10ebc5debfa81edb
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631839"
---
# <a name="bitsadmin-getpeercachingflags"></a>bitsadmin getpeercachingflags

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ジョブのファイルをキャッシュしてピアに提供できるかどうか、および BITS がピアからジョブのコンテンツをダウンロードできるかどうかを決定するフラグを取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getpeercachingflags <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのフラグを取得するには、次のようにします。

```
bitsadmin /getpeercachingflags myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
