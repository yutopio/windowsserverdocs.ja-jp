---
title: ftp lcd
description: Ftp lcd コマンドの参照記事。ローカルコンピューター上の作業ディレクトリを変更します。
ms.topic: reference
ms.assetid: 60a25808-6abb-408b-8373-0bbdcd0994b4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 91b2990495c91033c1bc885ec9d19142640f55b5
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621675"
---
# <a name="ftp-lcd"></a>ftp lcd

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ローカルコンピューター上の作業ディレクトリを変更します。 既定では、作業ディレクトリは、 **ftp** コマンドが開始されたディレクトリです。

## <a name="syntax"></a>構文

```
lcd [<directory>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `[<directory>]` | 変更するローカルコンピューター上のディレクトリを指定します。 *Directory*が指定されていない場合は、現在の作業ディレクトリが既定のディレクトリに変更されます。 |

### <a name="examples"></a>例

ローカルコンピューター上の作業ディレクトリを *c:\ dir1*に変更するには、次のように入力します。

```
lcd c:\dir1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
