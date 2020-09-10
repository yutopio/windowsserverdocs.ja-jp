---
title: ftp mdelete
description: Ftp mdelete コマンドの参照記事で、リモートコンピューター上のファイルを削除します。
ms.topic: reference
ms.assetid: 8a80a8f5-e880-40a8-abc9-29a41836844f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4b9ca1843fd405aef2a1c28c8b7f94bbc650f2d4
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627624"
---
# <a name="ftp-mdelete"></a>ftp mdelete

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートコンピューター上のファイルを削除します。

## <a name="syntax"></a>構文
```
mdelete <remotefile>[...]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<remotefile>` | 削除するリモートファイルを指定します。 |

### <a name="examples"></a>例

*a.exe*と*b.exe*のリモートファイルを削除するには、次のように入力します。

```
mdelete a.exe b.exe
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
