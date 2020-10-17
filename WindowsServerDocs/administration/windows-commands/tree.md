---
title: tree
description: ツリーの参照記事。パスのディレクトリ構造またはドライブ内のディスクをグラフィカルに表示します。
ms.topic: reference
ms.assetid: 345d3192-401e-4a3b-a8ac-36a85c7be79d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c9f586dbcf9072feffe71e1c3d792f10afc951a4
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156402"
---
# <a name="tree"></a>tree

ドライブのパスまたはディスクのディレクトリ構造をグラフィカルに表示します。 このコマンドによって表示される構造は、コマンドプロンプトで指定するパラメーターによって異なります。 ドライブまたはパスを指定しない場合、このコマンドを実行すると、現在のドライブの現在のディレクトリで始まるツリー構造が表示されます。

## <a name="syntax"></a>構文

```
tree [<drive>:][<path>] [/f] [/a]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<drive>:` | ディレクトリ構造を表示するディスクを含むドライブを指定します。 |
| `<path>` | ディレクトリ構造を表示するディレクトリを指定します。 |
| /f | 各ディレクトリ内のファイルの名前が表示されます。 |
| /a | サブディレクトリをリンクする行を表示するために、グラフィック文字の代わりにテキスト文字を使用するように指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>使用例

現在のドライブのディスクにあるすべてのサブディレクトリの名前を表示するには、次のように入力します。

```
tree \
```

一度に1つの画面を表示するには、C ドライブ上のすべてのディレクトリのファイルを次のように入力します。

```
tree c:\ /f | more
```

C ドライブのすべてのディレクトリの一覧を印刷するには、次のように入力します。

```
tree c:\ /f  prn
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
