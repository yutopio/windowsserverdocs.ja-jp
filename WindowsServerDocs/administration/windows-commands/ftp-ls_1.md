---
title: ftp ls
description: Ftp ls コマンドの参照記事。リモートコンピューターのファイルとサブディレクトリの省略形の一覧を表示します。
ms.topic: reference
ms.assetid: 5e03c7db-1e2b-419c-acb2-8a68f3db9615
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e1600c7664a61c417d8896467615717f968b01d4
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025756"
---
# <a name="ftp-ls"></a>ftp ls

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートコンピューターのファイルとサブディレクトリの省略形の一覧を表示します。

## <a name="syntax"></a>構文

```
ls [<remotedirectory>] [<localfile>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- |------------ |
| `[<remotedirectory>]` | 一覧を表示するディレクトリを指定します。 ディレクトリが指定されていない場合は、リモートコンピューター上の現在の作業ディレクトリが使用されます。 |
| `[<localfile>]` | 一覧を格納するローカル ファイルを指定します。 ローカルファイルが指定されていない場合、結果は画面に表示されます。 |

### <a name="examples"></a>例

リモートコンピューターのファイルとサブディレクトリの省略リストを表示するには、次のように入力します。

```
ls
```

リモートコンピューター上の *dir1* の省略形の一覧を取得し、それを *dirlist.txt*という名前のローカルファイルに保存するには、次のように入力します。

```
ls dir1 dirlist.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
