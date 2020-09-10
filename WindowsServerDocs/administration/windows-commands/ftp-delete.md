---
title: ftp delete
description: Ftp delete コマンドの参照記事。リモートコンピューター上のファイルを削除します。
ms.topic: reference
ms.assetid: 067c45f3-e4e8-4450-b8b6-836994f6adfe
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7a09e9abbe23582a2b5f2ba197a1877ffc62c7cc
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624795"
---
# <a name="ftp-delete"></a>ftp delete

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートコンピューター上のファイルを削除します。

## <a name="syntax"></a>構文

```
delete <remotefile>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<remotefile>` | 削除するファイルを指定します。 |

### <a name="examples"></a>例

リモートコンピューター上の *test.txt* ファイルを削除するには、次のように入力します。

```
delete test.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
