---
title: 型
description: テキストファイルの内容を表示する、type コマンドの参照記事です。
ms.topic: reference
ms.assetid: c44fe905-a865-4c97-8cc5-fb95fec7d4d5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.openlocfilehash: 879cd68b4995c65d623d56e97c0680587eda15b4
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156362"
---
# <a name="type"></a>型

Windows コマンドシェルの **type** は、テキストファイルの内容を表示する組み込みコマンドです。 **Type**コマンドを使用して、テキストファイルを変更せずに表示します。

PowerShell では、 **type** は [Get Content コマンドレット](/powershell/module/microsoft.powershell.management/get-content)の組み込みエイリアスであり、ファイルの内容も表示されますが、別の構文を使用します。

## <a name="syntax"></a>構文

```
type [<drive>:][<path>]<filename>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `[<drive>:][<path>]<filename>` | 表示するファイルの場所と名前を指定します。 に `<filename>` スペースが含まれている場合は、引用符で囲む必要があります (たとえば、"Spaces.txt を含む Filename")。 また、複数のファイル名の間にスペースを追加して追加することもできます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- プログラムによって作成されたバイナリファイルまたはファイルを表示すると、フォームフィード文字やエスケープシーケンスのシンボルなど、画面に奇妙な文字が表示されることがあります。 これらの文字は、バイナリファイルで使用される制御コードを表します。 一般に、バイナリファイルの表示には **type** コマンドを使用しないでください。

## <a name="examples"></a>使用例

*祭日*という名前のファイルの内容を表示するには、次のように入力します。

```
type holiday.mar
```

*祝日*という名前の長いファイルの内容を一度に1画面ずつ表示するには、次のように入力します。

```
type holiday.mar | more
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
