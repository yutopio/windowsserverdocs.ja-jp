---
title: setlocal
description: Setlocal コマンドのリファレンス記事。バッチファイルで環境変数のローカライズを開始します。
ms.topic: reference
ms.assetid: e4e4b6d3-3f1a-4851-a782-25ee2470e16e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2ad4e4c6bd023a5722d823a3bf67c5503329bda5
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389002"
---
# <a name="setlocal"></a>setlocal

バッチ ファイルで環境変数のローカライズを開始します。 ローカライズが一致するまで **endlocal** コマンドが見つかるまたはバッチ ファイルの末尾に到達します。

## <a name="syntax"></a>構文

```
setlocal [enableextensions | disableextensions] [enabledelayedexpansion | disabledelayedexpansion]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| 使って | 一致するまでコマンド拡張機能を有効 **endlocal** する前に設定に関係なく、コマンドが発生しました、 **setlocal** コマンドが実行されました。 |
| disableextensions | 一致するまでコマンド拡張機能を無効に **endlocal** する前に設定に関係なく、コマンドが発生しました、 **setlocal** コマンドが実行されました。 |
| enabledelayedexpansion | により、一致するまで遅延環境変数の拡張 **endlocal** する前に設定に関係なく、コマンドが発生しました、 **setlocal** コマンドが実行されました。 |
| disabledelayedexpansion | 一致するまで遅延環境変数の拡張を無効に **endlocal** する前に設定に関係なく、コマンドが発生しました、 **setlocal** コマンドが実行されました。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- **Setlocal**をスクリプトまたはバッチファイルの外部で使用すると、効果はありません。

- 使用 **setlocal** バッチ ファイルを実行すると、環境変数を変更します。 実行した後で変更した環境 **setlocal** バッチ ファイルに対してローカルです。 Cmd.exe プログラムが検出した場合に、以前の設定を復元する **endlocal** コマンドまたはバッチ ファイルの末尾に到達します。

- 1 つ以上を持つことができます **setlocal** または **endlocal** コマンド バッチ プログラム (つまり、入れ子になったコマンド) を実行します。

- **Setlocal** ERRORLEVEL 変数を設定します。 {**使って**  |  **disableextensions**} または {**enabledelayedexpansion**  |  **disabledelayedexpansion**} を渡した場合、ERRORLEVEL 変数は**0** (ゼロ) に設定されます。 それ以外の場合は、 **1**に設定されます。 バッチ スクリプトでこの情報を使用すると、次の例で示すように拡張機能は、使用できるかどうかを決定します。

    ```
    setlocal enableextensions
    verify other 2>nul
    if errorlevel 1 echo Unable to enable extensions
    ```

    **Cmd** コマンド拡張機能を無効にすると、ERRORLEVEL 変数を設定しない、 **確認** に無効な引数を使用する場合、コマンドを 0 以外の値を ERRORLEVEL 変数を初期化します。 またを使用する場合、 **setlocal** コマンドの引数に {**使って** | **disableextensions**} または {**enabledelayedexpansion** | **disabledelayedexpansion**} と、ERRORLEVEL 変数を設定しません **1**, 、コマンド拡張機能は使用できません。

## <a name="examples"></a>例

バッチファイル内の環境変数をローカライズするには、次のサンプルスクリプトに従います。

```
rem *******Begin Comment**************
rem This program starts the superapp batch program on the network,
rem directs the output to a file, and displays the file
rem in Notepad.
rem *******End Comment**************
@echo off
setlocal
path=g:\programs\superapp;%path%
call superapp>c:\superapp.out
endlocal
start notepad c:\superapp.out
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
