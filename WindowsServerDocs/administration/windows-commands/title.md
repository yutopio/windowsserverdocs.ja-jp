---
title: title
description: '[タイトル] コマンドの参照記事。コマンドプロンプトウィンドウのタイトルを作成します。'
ms.topic: reference
ms.assetid: c0bbe8bd-201a-4b6c-b617-5d9809881dc8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f4aaaf198a898589699547c522a734e9e3e5aba2
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156723"
---
# <a name="title"></a>title

コマンド プロンプト ウィンドウのタイトルを作成します。

## <a name="syntax"></a>構文

```
title [<string>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<string>` | コマンドプロンプトウィンドウのタイトルとして表示するテキストを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- バッチ プログラムのウィンドウのタイトルを作成するには、 **タイトル** バッチ ファイルの先頭にあるコマンドです。

- ウィンドウのタイトルを設定した後のみを使用してリセットできます、 **タイトル** コマンドです。

## <a name="examples"></a>使用例

バッチファイルで [**コピー** ] コマンドを実行してから、 *[コマンドプロンプト*] ウィンドウのタイトルを変更して*ファイルを更新*するには、次のスクリプトを入力します。

```
@echo off
title Updating Files
copy \\server\share\*.xls c:\users\common\*.xls
echo Files Updated.
title Command Prompt
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
