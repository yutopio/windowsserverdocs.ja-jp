---
title: ftp mput
description: Ftp mput コマンドの参照記事。現在のファイル転送の種類を使用してローカルファイルをリモートコンピューターにコピーします。
ms.topic: reference
ms.assetid: 980f15e7-7cf1-4813-9946-a8cc4edfb198
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: cd799e713b71f23c7ce22a9ee81dc19cd78f8c31
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635312"
---
# <a name="ftp-mput"></a>ftp mput

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

転送の種類を現在のファイルを使用してリモート コンピューターにローカル ファイルをコピーします。

## <a name="syntax"></a>構文

```
mput <localfile>[ ]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<localfile>` | リモート コンピューターにコピーするローカル ファイルを指定します。 |

### <a name="examples"></a>例

現在のファイル転送の種類を使用して *Program1.exe* および *Program2.exe* をリモートコンピューターにコピーするには、次のように入力します。

```
mput Program1.exe Program2.exe
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ftp ascii コマンド](ftp-ascii.md)

- [ftp バイナリコマンド](ftp-binary.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
