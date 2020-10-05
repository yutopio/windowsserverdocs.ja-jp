---
title: start
description: 指定したプログラムまたはコマンドを実行するための個別のコマンドプロンプトウィンドウを開始する、start コマンドの参照記事。
ms.topic: reference
ms.assetid: 0173f9b3-5cd7-4edb-b01e-d02193b4fadc
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6c154cd0c3cab4520f64c77d2ecc920dfc8bdcc9
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718269"
---
# <a name="start"></a>start

指定したプログラムまたはコマンドを実行する別のコマンド プロンプト ウィンドウを起動します。

## <a name="syntax"></a>構文

```
start [<title>] [/d <path>] [/i] [{/min | /max}] [{/separate | /shared}] [{/low | /normal | /high | /realtime | /abovenormal | belownormal}] [/affinity <hexaffinity>] [/wait] [/elevate] [/b] [<command> [<parameter>... ] | <program> [<parameter>... ]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<title>` | **コマンドプロンプト**ウィンドウのタイトルバーに表示するタイトルを指定します。 |
| d `<path>` | スタートアップ ディレクトリを指定します。 |
| /i | Cmd.exe スタートアップ環境を新しい **コマンドプロンプト** ウィンドウに渡します。 場合 **/i** が指定されていない、現在の環境を使用します。 |
| `{/min | /max}` | 新しい**コマンドプロンプト**ウィンドウを最小化 (**/分**) するか、最大化する (**/最大**) ことを指定します。 |
| `{/separate | /shared}` | 別のメモリ領域で 16 ビット プログラムを起動 (**/separate**) または共有メモリの領域 (**/共有**)。 64 ビット プラットフォームでは、これらのオプションはサポートされていません。 |
| `{/low | /normal | /high | /realtime | /abovenormal | belownormal}` | 指定した優先度クラスでは、アプリケーションを起動します。 |
| /アフィニティ `<hexaffinity>` | 新しいアプリケーションを (16 進数として表されます)、指定されたプロセッサ関係マスクを適用します。 |
| /wait | アプリケーションを起動し、終了するまで待機します。 |
| /昇格 | 管理者としてアプリケーションを実行します。 |
| /b | 新しい **コマンドプロンプト** ウィンドウを開かずにアプリケーションを起動します。 CTRL キーを押しながら C キーの処理には、アプリケーションは CTRL + C 処理を有効にしない限りは無視されます。 アプリケーションを中断するのにには、CTRL キーを押しながら BREAK キーを使用します。 |
| `[<command> [<parameter>... ] | <program> [<parameter>... ]]` | 開始するコマンドまたはプログラムを指定します。 |
| `<parameter>` | コマンドまたはプログラムに渡すパラメーターを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- ファイルの関連付けを使用して、ファイルの名前をコマンドとして入力することで、非実行可能ファイルを実行できます。

- 拡張子またはパスの修飾子を含まない最初のトークンとして文字列 CMD を含むコマンドを実行すると、CMD は COMSPEC 変数の値に置き換えられます。 これを取得できないように **cmd** 、現在のディレクトリからです。

- 32ビットのグラフィカルユーザーインターフェイス (GUI) アプリケーションを実行する場合、コマンドプロンプトに戻る前に、アプリケーションが終了するのを **cmd** は待機しません。 この動作は、コマンド スクリプトからアプリケーションを実行する場合に発生しません。

- 拡張機能が含まれていない最初のトークンを使用するコマンドを実行すると、Cmd.exe は PATHEXT 環境変数の値を使用して、検索する拡張機能とその順序を決定します。 PATHEXT 変数の既定値は、します。

  ```
  .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.MSC
  ```

  構文は PATH 変数と同じであり、セミコロン (;)各拡張機能を区切ります。

- 実行可能ファイルを検索するときに、どの拡張機能にも一致するものがない場合は、によって、名前がディレクトリ名と一致するかどうか **が確認さ** れます。 そのような場合は、 **開始** そのパスに Explorer.exe を開きます。

## <a name="examples"></a>例

コマンドプロンプトで *Myapp* プログラムを起動し、現在の **コマンドプロンプト** ウィンドウの使用を保持するには、次のように入力します。

```
start Myapp
```

個別に最大化された**コマンドプロンプト**ウィンドウで**start**コマンドラインヘルプトピックを表示するには、次のように入力します。

```
start /max start /?
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
