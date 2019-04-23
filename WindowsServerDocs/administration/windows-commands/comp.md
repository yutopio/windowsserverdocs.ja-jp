---
title: comp
description: 'Windows コマンド」のトピック * * *- '
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 40319d23-704d-4da1-be93-8259547275d0
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d10b86176d97e1afd76085516fbfc00bdc36577f
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59854683"
---
# <a name="comp"></a>comp



2 つのファイルの内容またはバイトごとのセットを比較します。 パラメーターを指定せずに使用されている場合**comp**比較対象のファイルを入力するように求められます。

このコマンドを使用する方法の例については、[例](#BKMK_examples)を参照してください。

## <a name="syntax"></a>構文

```
comp [<Data1>] [<Data2>] [/d] [/a] [/l] [/n=<Number>] [/c]
```

## <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|\<Data1 >|比較するファイルの場所と、最初のファイルの名前を指定します。 ワイルドカード文字を使用することができます (**&#42;** と **?**) を複数のファイルを指定します。|
|\<Data2 >|比較するファイルの場所と 2 番目のファイルの名前を指定します。 ワイルドカード文字を使用することができます (**&#42;** と **?**) を複数のファイルを指定します。|
|/d|10 進形式の相違を表示します。 (既定の形式は、16 進数)。|
|/a|違いは、文字として表示します。|
|/l|バイト オフセットを表示する代わりに、違いが発生する行の数が表示されます。|
|/n =\<番号 >|ファイルはサイズが異なる場合でも、ファイルごとに指定されている行の数のみを比較します。|
|/c|大文字小文字を区別しない比較を行います。|
|/[オフライン]|オフライン属性が設定されたファイルを処理します。|
|/?|コマンド プロンプトでヘルプを表示します。|

## <a name="remarks"></a>注釈

-   どの**comp**コマンドは、一致していない情報を識別します。

    比較中に**comp**ファイル間で一致しない情報の場所を識別するメッセージが表示されます。 各メッセージは、等しくないバイトのオフセットのメモリ アドレスおよびバイトの内容を示します (16 進数表記でない限り、 **/a**または **/d**コマンド ライン パラメーターを指定)。 次の形式でメッセージが表示されます。

    `Compare error at OFFSET xxxxxxxx`

    `file1 = xx`

    `file2 = xx`

    10 個の等しくない比較後**comp**ファイルの比較を停止し、次のメッセージが表示されます。

    `10 Mismatches - ending compare`
-   特殊なケースを処理*Data1*と*Data2*  
    -   必要なコンポーネントのいずれかを省略した場合*Data1*または*Data2*を省略した場合または*Data2*、 **comp**不足している情報をユーザーに求めます。
    -   場合*Data1*ドライブ文字のみまたはファイル名がないディレクトリ名を含む**comp**すべてで指定されたファイルに指定されたディレクトリ内のファイルと比較*Data1*します。
    -   場合*Data2*ドライブ文字のみまたはディレクトリ名、既定のファイル名を含む*Data2*ことと同じ*Data1*。
    -   場合**comp**で複数のファイルを比較するかどうかを判別するメッセージを求め、指定したファイルを見つけることができません。
-   別の場所にファイルを比較します。

    **Comp**同じドライブに別のドライブと同じディレクトリにまたは異なるディレクトリにファイルを比較できます。 ときに**comp**ファイルを比較し、場所とファイル名が表示されます。
-   同じ名前のファイルを比較します。

    比較するファイルは、別のディレクトリまたは複数のドライブにある場合は、同じファイル名を持つことができます。 ファイル名を指定しない場合*Data2*、既定のファイル名を*Data2*内のファイル名と同じ*Data1*します。 ワイルドカード文字を使用することができます (**&#42;** と **?**) ファイル名を指定します。
-   さまざまなサイズのファイルを比較します。

    指定する必要があります **/n**さまざまなサイズのファイルを比較します。 ファイルのサイズが異なる場合と **/n**が指定されていない**comp**次のメッセージが表示されます。

    `Files are different sizes`

    `Compare more files (Y/N)?`

    これらのファイルを比較する N キーを押して、停止、 **comp**コマンド。 次に、再実行、 **comp**コマンドを **/n**各ファイルの最初の部分のみを比較するオプション。
-   ファイルを順番に比較します。

    ワイルドカード文字を使用する場合 (**&#42;** と **?**) 複数のファイルを指定する**comp**と一致する最初のファイルを検索します*Data1*で対応するファイル比較*Data2*存在します場合。 **Comp**コマンドは、一致する各ファイルの比較の結果を報告*Data1*します。 完了したら、 **comp**次のメッセージが表示されます。

    `Compare more files (Y/N)?`

    さらにファイルを比較するには、Y キーを押します。**Comp**コマンドは、場所と新しいファイルの名前を要求します。 停止、比較を実行する N キーを押しますY キーを押す**comp**コマンド ライン オプションを使用するためのメッセージが表示されます。 任意のコマンド ライン オプションを指定しない場合**comp**する前に指定したものを使用します。

## <a name="BKMK_examples"></a>例

ディレクトリ C:\Reports とバックアップ ディレクトリの内容を比較する\\ \\Sales\Backup\April、種類。
```
comp c:\reports \\sales\backup\april
```
\Invoice ディレクトリ内のテキスト ファイルの最初の 10 個の行を比較し、10 進数形式で結果を表示、入力します。
```
comp \invoice\*.txt \invoice\backup\*.txt /n=10 /d
```

#### <a name="additional-references"></a>その他の参照情報

[コマンドライン構文キー](command-line-syntax-key.md)