---
title: 型
description: テキストファイルの内容を表示する型の参照記事です。
ms.topic: reference
ms.assetid: c44fe905-a865-4c97-8cc5-fb95fec7d4d5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.openlocfilehash: 7b944037c6dc73de89fa92b54a41b07ff09fcf69
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626661"
---
# <a name="type"></a>型

Windows コマンドシェルの **type** は、テキストファイルの内容を表示する組み込みコマンドです。 **Type**コマンドを使用して、テキストファイルを変更せずに表示します。

PowerShell では、 **type** は **[Get Content](/powershell/module/microsoft.powershell.management/get-content)** コマンドレットへの組み込みエイリアスであり、ファイルの内容も表示されますが、構文は異なります。

## <a name="syntax"></a>構文

```
type [<Drive>:][<Path>]<FileName>
```

### <a name="parameters"></a>パラメーター

|パラメーター|Description|
|---------|-----------|
|[\<Drive>:][\<Path>]\<FileName>|表示するファイルの場所と名前を指定します。 複数のファイル名をスペースで区切ります。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>注釈

-   *FileName*にスペースが含まれている場合は、引用符で囲みます (たとえば、Spaces.txt を含むファイル名)。
-   プログラムによって作成されたバイナリファイルまたはファイルを表示すると、フォームフィード文字やエスケープシーケンスのシンボルなど、画面に奇妙な文字が表示されることがあります。 これらの文字は、バイナリファイルで使用される制御コードを表します。 一般に、バイナリファイルの表示には **type** コマンドを使用しないでください。

## <a name="examples"></a>例

祭日という名前のファイルの内容を表示するには、次のように入力します。
```
type holiday.mar
```
祝日という名前の長いファイルの内容を一度に1画面ずつ表示するには、次のように入力します。
```
type holiday.mar | more
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
