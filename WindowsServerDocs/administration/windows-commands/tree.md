---
title: tree
description: ツリーの参照記事。パスのディレクトリ構造またはドライブ内のディスクをグラフィカルに表示します。
ms.topic: reference
ms.assetid: 345d3192-401e-4a3b-a8ac-36a85c7be79d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c164fe8999313ffd40ec12b29c7ad8cf2bd7c7a5
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026890"
---
# <a name="tree"></a>tree

ドライブのパスまたはディスクのディレクトリ構造をグラフィカルに表示します。



## <a name="syntax"></a>構文

```
tree [<Drive>:][<Path>] [/f] [/a]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|\<Drive>:|ディレクトリ構造を表示するディスクを含むドライブを指定します。|
|\<Path>|ディレクトリ構造を表示するディレクトリを指定します。|
|/f|各ディレクトリ内のファイルの名前が表示されます。|
|/a|**ツリー**で、サブディレクトリをリンクする行を表示するために、グラフィック文字の代わりにテキスト文字を使用することを指定します。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>解説

**ツリー**によって表示される構造は、コマンドプロンプトで指定するパラメーターによって異なります。 ドライブまたはパスを指定しない場合は、現在のドライブの現在のディレクトリで始まるツリー構造が **ツリー** に表示されます。

## <a name="examples"></a>例

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

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)