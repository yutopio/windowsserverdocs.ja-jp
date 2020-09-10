---
title: bitsadmin peercaching および setconfigurationflags
description: Bitsadmin のピアリングと setconfigurationflags コマンドのリファレンス記事。コンピューターがコンテンツをピアに提供できるかどうか、およびピアからコンテンツをダウンロードできるかどうかを決定する構成フラグを設定します。
ms.topic: reference
ms.assetid: ff0a2b49-66e3-4d40-824c-6a3816055d2e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 73daad6a915ee39f166d54efd79290ce92df60db
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631343"
---
# <a name="bitsadmin-peercaching-and-setconfigurationflags"></a>bitsadmin peercaching および setconfigurationflags

コンピューターがピアにコンテンツを提供できるかどうか、およびピアからコンテンツをダウンロードできるかどうかを決定する構成フラグを設定します。

## <a name="syntax"></a>構文

```
bitsadmin /peercaching /setconfigurationflags <job> <value>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| 値 | バイナリ表現のビットを次のように解釈する符号なし整数。<ul><li>ジョブのデータをピアからダウンロードできるようにするには、最下位ビットを設定します。</li><li>ジョブのデータをピアに配信できるようにするには、右側の2番目のビットを設定します。</li></ul>|

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブについて、ピアからダウンロードするジョブのデータを指定するには、次のようにします。

```
bitsadmin /peercaching /setconfigurationflags myDownloadJob 1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)

- [bitsadmin ピアキャッシュコマンド](bitsadmin-peercaching.md)
