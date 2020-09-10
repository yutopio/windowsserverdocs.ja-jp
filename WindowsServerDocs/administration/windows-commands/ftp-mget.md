---
title: ftp mget
description: 現在のファイル転送の種類を使用してリモートファイルをローカルコンピューターにコピーする、ftp mget コマンドの参照記事です。
ms.topic: reference
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ca56e43df4a03fd52f8028d390cb2da62901ca06
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89621625"
---
# <a name="ftp-mget"></a>ftp mget

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

転送の種類を現在のファイルを使用してローカル コンピューターにリモート ファイルをコピーします。

## <a name="syntax"></a>構文

```
mget <remotefile>[ ]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<remotefile>` | ローカル コンピューターにコピーするリモート ファイルを指定します。 |

### <a name="examples"></a>例

現在のファイル転送の種類を使用してリモートファイル *a.exe* および *b.exe* をローカルコンピューターにコピーするには、次のように入力します。

```
mget a.exe b.exe
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ftp ascii コマンド](ftp-ascii.md)

- [ftp バイナリコマンド](ftp-binary.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
