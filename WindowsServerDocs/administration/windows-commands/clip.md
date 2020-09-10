---
title: clip
description: コマンドの出力をコマンドラインから Windows クリップボードにリダイレクトする、clip コマンドの参照記事。
ms.topic: reference
ms.assetid: 85322d85-3376-4806-845b-93ac77fe27bf
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9f6820d60a8c94ed07bbb23bbbd86be3f1f289b7
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629628"
---
# <a name="clip"></a>clip

コマンドの出力をコマンドラインから Windows クリップボードにリダイレクトします。 このコマンドを使用すると、クリップボードからテキストを受信できる任意のアプリケーションにデータを直接コピーできます。 また、このテキスト出力を他のプログラムに貼り付けることもできます。

## <a name="syntax"></a>構文

```
<command> | clip
clip < <filename>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<command>` | 出力を Windows クリップボードに送信するコマンドを指定します。 |
| `<filename>` | Windows クリップボードに送信する内容を含むファイルを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

現在のディレクトリの一覧を Windows クリップボードにコピーするには、次のように入力します。

```
dir | clip
```

*汎用*のプログラムの出力を Windows クリップボードにコピーするには、次のように入力します。

```
awk -f generic.awk input.txt | clip
```

*readme.txt*という名前のファイルの内容を Windows クリップボードにコピーするには、次のように入力します。

```
clip < readme.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)