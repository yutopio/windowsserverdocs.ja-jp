---
title: ftp recv
description: 現在のファイル転送の種類を使用してリモートファイルをローカルコンピューターにコピーする、ftp の recv コマンドに関するリファレンス記事です。
ms.topic: reference
ms.assetid: f249ce61-247d-421b-9b93-48bce5108800
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2a80c00c99df3466fc1077c3a09cab29f9e59860
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038913"
---
# <a name="ftp-recv"></a>ftp recv

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

現在のファイル転送の種類を使用して、リモートファイルをローカルコンピューターにコピーします。

> [!NOTE]
> このコマンドは、 [ftp の get コマンド](ftp-get.md)と同じです。

## <a name="syntax"></a>構文

```
recv <remotefile> [<localfile>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<remotefile>` | コピーするリモートファイルを指定します。 |
| `[<localfile>]` | ローカルコンピューターで使用するファイルの名前を指定します。 *Localfile*が指定されていない場合、ファイルには*remotefile*の名前が付けられます。 |

### <a name="examples"></a>例

現在のファイル転送を使用して *test.txt* をローカルコンピューターにコピーするには、次のように入力します。

```
recv test.txt
```

現在のファイル転送を使用して*test1.txt*としてローカルコンピューターに*test.txt*をコピーするには、次のように入力します。

```
recv test.txt test1.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ftp get コマンド](ftp-get.md)

- [ftp ascii コマンド](ftp-ascii.md)

- [ftp バイナリコマンド](ftp-binary.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
