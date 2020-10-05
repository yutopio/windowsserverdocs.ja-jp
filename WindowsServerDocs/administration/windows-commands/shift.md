---
title: shift
description: バッチファイル内のバッチパラメーターの位置を変更する、shift コマンドの参照記事です。
ms.topic: reference
ms.assetid: b56574e8-570a-4cc9-bbac-1b94fbf6a47a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4553826aa7c3def335ae1d9ec9594ee9d878fc63
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718339"
---
# <a name="shift"></a>shift

バッチ ファイル内のバッチのパラメーターの位置を変更します。

## <a name="syntax"></a>構文

```
shift [/n <N>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| ms-dos `<N>` | *N*番目の引数からシフトを開始するように指定します。ここで、 *n*は*0* ~ *8*の任意の値です。 既定で有効になっているコマンド拡張機能が必要です。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="remarks"></a>解説

- **Shift キーを押し** コマンド バッチのパラメーターの値を変更する **%0** を通じて **%9** 前に各パラメーターをコピーして: の値 **%1** にコピー **%0**, の値 **%2** にコピー **%1**, 、という具合です。 これは、パラメーターの数にかかわらず、同じ操作を実行するバッチ ファイルを作成するため便利です。

- コマンド拡張機能が有効になっている場合、 **shift** コマンドをサポートする、 **/n** コマンド ライン オプションです。 **/N** n 番目の引数で移行を開始するオプションが指定場所 **N** は 8 ~ 0 の値。 など **SHIFT/2** 移動することに **%3** に **%2**, 、**%4** に **%3**, のままにし、 **%0** と **%1** 影響はありません。 既定では、コマンド拡張機能が有効にします。

- 使用することができます、 **shift** 10 個を超えるバッチ パラメーターを受け取りが可能なバッチ ファイルを作成するコマンドです。 コマンドラインで複数の 10 個のパラメーターを指定する場合、表示される、10 分後に (**%9**) には、一度に 1 つのシフトをする **%9**します。

- **Shift**コマンドを実行しても、バッチパラメーターには影響しません **%\*** 。

- 後方 **シフト** コマンドはありません。 **Shift**コマンドを実装した後、シフトの前に存在していたバッチパラメーター (**%0**) を復旧することはできません。

## <a name="examples"></a>例

*Mycopy.bat*と呼ばれるバッチファイルを使用して、ファイルの一覧を特定のディレクトリにコピーするには、次のように入力します。

```
@echo off
rem MYCOPY.BAT copies any number of files
rem to a directory.
rem The command uses the following syntax:
rem mycopy dir file1 file2 ...
set todir=%1
:getfile
shift
if %1== goto end
copy %1 %todir%
goto getfile
:end
set todir=
echo All done
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
