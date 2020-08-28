---
title: ftp mget
description: 現在のファイル転送の種類を使用してリモートファイルをローカルコンピューターにコピーする、ftp mget コマンドの参照記事です。
ms.topic: reference
ms.assetid: 6c85ae96-ec51-48a9-a227-7f02c7332c69
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e72d253fec35f366e2ab80a491c256e0de6c948f
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025746"
---
# <a name="ftp-mget"></a>ftp mget

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

転送の種類を現在のファイルを使用してローカル コンピューターにリモート ファイルをコピーします。

## <a name="syntax"></a>構文

```
mget <remotefile>[ ]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
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
