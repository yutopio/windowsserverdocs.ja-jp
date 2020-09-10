---
title: ftp rename
description: リモートファイルの名前を変更する ftp rename コマンドの参照記事です。
ms.topic: reference
ms.assetid: 977b7c95-6428-4980-80ec-79c3ae7e8c4d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ea7862a759779a5f767b8e18cdd5a0b36db2a6a1
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627630"
---
# <a name="ftp-rename"></a>ftp rename

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートファイルの名前を変更します。

## <a name="syntax"></a>構文

```
rename <filename> <newfilename>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<filename>` | 名前を変更するファイルを指定します。 |
| `<newfilename>` | 新しいファイル名を指定します。 |

### <a name="examples"></a>例

リモートファイル *example.txt* の名前を *example1.txt*に変更するには、次のように入力します。

```
rename example.txt example1.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
