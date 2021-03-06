---
title: rem
description: Rem コマンドの参照記事。スクリプト、バッチ、または config.sys ファイルにコメントを記録します。
ms.topic: reference
ms.assetid: 1a45b585-a83c-4ff6-badd-ff40f34cec23
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c56595a45eba3fd841f1f455c189164b240191e8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640647"
---
# <a name="rem"></a>rem

スクリプト、バッチ、または config.sys ファイルにコメントを記録します。 コメントが指定されていない場合 **rem** の上下の間隔を追加します。

## <a name="syntax"></a>構文

```
rem [<comment>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<comment>` | コメントとして追加する文字の文字列を指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- **Rem**コマンドを実行しても、画面にコメントは表示されません。 画面にコメントを表示するには、ファイルに **echo on** コマンドを含める必要があります。

- `<`バッチファイルコメントにリダイレクト文字 (または `>` ) またはパイプ () を使用することはできません `|` 。

- 使用できますが **rem** 、コメントの上下の間隔をバッチ ファイルに追加することがなく、空白行を使用することもできます。 バッチ ファイルが処理されるときに、空白行は無視されます。

### <a name="examples"></a>例

バッチファイルのコメントを使用して上下の間隔を追加するには、次のように入力します。

```
@echo off
rem  This batch program formats and checks new disks.
rem  It is named Checknew.bat.
rem
rem echo Insert new disk in Drive B.
pause
format b: /v chkdsk b:
```

config.sys ファイルの **prompt** コマンドの前に説明のコメントを含めるには、次のように入力します。

```
rem Set prompt to indicate current directory
prompt $p$g
```

スクリプトの内容に関するコメントを入力するには、次のように入力します。

```
rem The commands in this script set up 3 drives.
rem The first drive is a primary partition and is
rem assigned the letter D. The second and third drives
rem are logical partitions, and are assigned letters
rem E and F.
create partition primary size=2048
assign d:
create partition extended
create partition logical size=2048
assign e:
create partition logical
assign f:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)