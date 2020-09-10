---
title: bitsadmin peercaching および getconfigurationflags
description: Bitsadmin ピアリングと getconfigurationflags コマンドの参照記事。コンピューターがピアにコンテンツを提供するかどうか、およびピアからコンテンツをダウンロードできるかどうかを決定する構成フラグを取得します。
ms.topic: reference
ms.assetid: 124ddc15-3444-4bd5-96e5-c6bfabe4f9c2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3fe1adfb44ab845ecdb73222131191782f83c075
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631373"
---
# <a name="bitsadmin-peercaching-and-getconfigurationflags"></a>bitsadmin peercaching および getconfigurationflags

コンピューターがピアにコンテンツを提供するかどうか、およびピアからコンテンツをダウンロードできるかどうかを決定する構成フラグを取得します。

## <a name="syntax"></a>構文

```
bitsadmin /peercaching /getconfigurationflags <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの構成フラグを取得するには、次のようにします。

```
bitsadmin /peercaching /getconfigurationflags myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)

- [bitsadmin ピアキャッシュコマンド](bitsadmin-peercaching.md)
