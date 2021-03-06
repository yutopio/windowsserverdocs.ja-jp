---
title: dir
description: ディレクトリのファイルとサブディレクトリの一覧を表示する dir コマンドの参照記事です。
ms.topic: reference
ms.assetid: edcbf69b-eaa4-466e-b210-3dd8892f4d93
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c5edcbaac04d6f87721644fb4943e75456a21f66
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634993"
---
# <a name="dir"></a>dir

ディレクトリのファイルとサブディレクトリの一覧を表示します。 パラメーターを指定せずに使用した場合、ディスクのボリュームラベルとシリアル番号の後にディスク上のディレクトリとファイルの一覧が表示されます (それぞれの名前と最後に変更された日付と時刻を含む)。 ファイルの場合、このコマンドは、名前の拡張子とサイズをバイト単位で表示します。 このコマンドでは、表示されているファイルとディレクトリの総数、その累積サイズ、ディスクの空き領域 (バイト単位) も表示されます。

**Dir**コマンドは、別のパラメーターを使用して Windows 回復コンソールから実行することもできます。 詳細については、「 [Windows 回復環境 (WinRE)](/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)」を参照してください。

## <a name="syntax"></a>構文

```
dir [<drive>:][<path>][<filename>] [...] [/p] [/q] [/w] [/d] [/a[[:]<attributes>]][/o[[:]<sortorder>]] [/t[[:]<timefield>]] [/s] [/b] [/l] [/n] [/x] [/c] [/4] [/r]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `[<drive>:][<path>]` | 一覧を表示するドライブとディレクトリを指定します。 |
| `[<filename>]` | 一覧を表示する特定のファイルまたはファイルのグループを指定します。 |
| /p | 一覧の1つの画面を一度に表示します。 次の画面を表示するには、任意のキーを押します。 |
| /q | ファイルの所有権情報を表示します。 |
| /w | 一覧をワイド形式で表示します。最大で5つのファイル名またはディレクトリ名が各行に表示されます。 |
| /d | 一覧を **/w**と同じ形式で表示しますが、ファイルは列で並べ替えられます。 |
| /a [[:] `<attributes>` ] | 指定した属性を持つディレクトリとファイルの名前のみを表示します。 このパラメーターを使用しない場合、コマンドを実行すると、隠しファイルとシステムファイルを除くすべてのファイルの名前が表示されます。 *属性*を指定せずにこのパラメーターを使用すると、隠しファイルやシステムファイルなど、すべてのファイルの名前が表示されます。 使用可能な *属性* 値の一覧は次のとおりです。<ul><li>**d** -ディレクトリ</li><li>**h** -非表示ファイル</li><li>**s** -システムファイル</li><li>**l** -再解析ポイント</li><li>**r** -読み取り専用ファイル</li><li>**a** -アーカイブの準備ができているファイル</li><li>**i** -インデックスが作成されていないファイル</li></ul>これらの値の任意の組み合わせを使用できますが、スペースを使用して値を区切ることはできません。 必要に応じて、コロン (:) を使用することもできます。区切り記号。ハイフン (-) をプレフィックスとして使用して、"not" を意味します。 たとえば、 **-s** 属性を使用してもシステムファイルは表示されません。 |
| /o [[:] `<sortorder>` ] | 並べ替え *順序*に従って出力を並べ替えます。次の値の任意の組み合わせを指定できます。<ul><li>**n** -名前でアルファベット順</li><li>**e** -拡張子別のアルファベット順</li><li>**g** -ディレクトリを最初にグループ化する</li><li>**s** -サイズ、最小値順</li><li>最初**の日付**/時刻 (最も古い順)</li><li>プレフィックスを使用して **-** 並べ替え順序を逆にする</li></ul>複数の値は、一覧の順序に従って処理されます。 複数の値をスペースで区切るのではなく、必要に応じてコロン (:) を使用することもできます。<p>*順序*付けが指定されていない場合、ディレクトリはアルファベット順**に一覧表示**され、ファイルもアルファベット順に並べ替えられます。 |
| /t [[:] `<timefield>` ] | 表示または並べ替えに使用する時間フィールドを指定します。 使用できる *timefield* 値は次のとおりです。<ul><li>**c** -作成</li><li>**-最終** アクセス日時</li><li>**w** -最終書き込み</li></ul> |
| /s | 指定したディレクトリとすべてのサブディレクトリ内で、指定したファイル名が出現するたびに一覧表示します。 |
| /b | ディレクトリとファイルの一覧を表示します。追加情報は含まれません。 **/B**パラメーターは **/w**をオーバーライドします。 |
| /l | 並べ替えられていないディレクトリ名とファイル名を小文字で表示します。 |
| /n | 画面の右端にファイル名を含む長いリスト形式が表示されます。 |
| /x | 非8dot3 ファイル名に対して生成される短い名前を表示します。 表示は **/n**の表示と同じですが、短い名前は長い名前の前に挿入されます。 |
| /c | ファイルサイズで桁区切り記号を表示します。 これは既定の動作です。 区切り記号を非表示にするには **/c** を使用します。 |
| /4 | 年を4桁の形式で表示します。 |
| /r | ファイルの代替データストリームを表示します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- 複数の *filename* パラメーターを使用するには、各ファイル名をスペース、コンマ、またはセミコロンで区切ります。

- ワイルドカード文字 (**&#42;** または **?**) を使用して、ファイル名の1つ以上の文字を表すことや、ファイルまたはサブディレクトリのサブセットを表示することができます。

- ワイルドカード文字 ( **&#42;**) を使用すると、次のように任意の文字列を置き換えることができます。

  - `dir *.txt` 現在のディレクトリにあるファイルのうち、.txt で始まる拡張子 (.txt、txt1、. txt_old など) をすべて一覧表示します。

  - `dir read *.txt` 現在のディレクトリにあるすべてのファイルを一覧表示、読み取りと拡張子 .txt で始まる拡張子 .txt,、txt1,、または. txt_old です。

  - `dir read *.*` 現在のディレクトリにあるすべてのファイルを一覧表示します。読み取りは任意の拡張子で開始します。

  アスタリスクのワイルドカードでは、常に短いファイル名マッピングが使用されるため、予期しない結果が発生する可能性があります。 たとえば、次のディレクトリには2つのファイル (t.txt2 と t97.txt) が含まれています。

  ```
  C:\test>dir /x
  Volume in drive C has no label.
  Volume Serial Number is B86A-EF32

  Directory of C:\test

  11/30/2004  01:40 PM <DIR>  .
  11/30/2004  01:40 PM <DIR> ..
  11/30/2004  11:05 AM 0 T97B4~1.TXT t.txt2
  11/30/2004  01:16 PM 0 t97.txt
  ```

  入力によって t97.txt ファイルが返されることが予想される場合があり `dir t97\*` ます。 ただし、入力すると、両方のファイルが返されます `dir t97\*` 。これは、アスタリスクのワイルドカードがファイル t.txt2 に一致し、短い名前マップ *T97B4 ~1.TXT*を使用して t97.txt されるためです。 同様に、「」と入力する `del t97\*` と、両方のファイルが削除します。

- 名前の1文字の代わりに疑問符 (?) を使用できます。 たとえば、「」と入力すると、 `dir read???.txt` 現在のディレクトリにあるファイルのうち、read で始まる拡張子 .txt が使用され、その後に最大3文字が続きます。 これには、Read.txt、Read1.txt、Read12.txt、Read123.txt、Readme1.txt が含まれますが、Readme12.txt は含まれません。

- *属性*に複数の値を指定して **/a**を使用する場合、このコマンドを実行すると、指定したすべての属性を持つファイルのみの名前が表示されます。 たとえば、またはのいずれかを使用して、 **r**と **-h**を含む **/a**を属性として使用する場合 `/a:r-h` `/ar-h` 、このコマンドでは、非表示になっていない読み取り専用ファイルの名前のみが表示されます。

- *複数の並べ替え値を*指定した場合、このコマンドは、最初の条件 (2 番目の条件) によってファイル名を並べ替えます。 たとえば、またはのいずれかを使用して、(または) を使用して、 **パラメーターに** **e** と **-s** *を使用* した場合、 `/o:e-s` `/oe-s` このコマンドはディレクトリとファイルの名前を拡張によって順に並べ替え、最後の結果を表示します。 拡張子によるアルファベット順の並べ替えでは、拡張子のないファイル名、ディレクトリ名、拡張子を持つファイル名が先頭に表示されます。

- リダイレクトシンボル () を使用して `>` このコマンドの出力をファイルに送信する場合、またはパイプ () を使用して `|` このコマンドの出力を別のコマンドに送信する場合は、 `/a:-d` と **/b** を使用してファイル名のみを一覧表示する必要があります。 **/B**および **/s**と共に*filename*を使用すると、このコマンドが、ファイル名に一致するすべてのファイル名の現在のディレクトリとそのサブディレクトリを検索するように指定*できます。* このコマンドは、検出された各ファイル名について、ドライブ文字、ディレクトリ名、ファイル名、およびファイル名拡張子 (1 行につき1つのパス) のみを一覧表示します。 パイプを使用してこのコマンドの出力を別のコマンドに送信する前に、Autoexec.bat ファイルで *TEMP* 環境変数を設定する必要があります。

## <a name="examples"></a>例

すべてのディレクトリを1つずつ表示するには (アルファベット順、ワイド形式)、各画面の後に一時停止するには、ルートディレクトリが現在のディレクトリであることを確認し、次のように入力します。

```
dir /s/w/o/p
```

出力には、ルートディレクトリ、サブディレクトリ、およびルートディレクトリ内のファイル (拡張子を含む) が表示されます。 このコマンドでは、ツリー内の各サブディレクトリのサブディレクトリ名とファイル名も一覧表示されます。

前の例を変更して、ファイル名と拡張子を **dir** に表示させるようにしますが、ディレクトリ名を省略するには、次のように入力します。

```
dir /s/w/o/p/a:-d
```

ディレクトリの一覧を印刷するには、次のように入力します。

```
dir > prn
```

**Prn**を指定すると、ディレクトリリストは LPT1 ポートに接続されているプリンターに送信されます。 プリンターが別のポートに接続されている場合は、 **prn** を正しいポートの名前に置き換える必要があります。

また、 **prn**をファイル名に置き換えて、 **dir**コマンドの出力をファイルにリダイレクトすることもできます。 パスを入力することもできます。 たとえば、ファイル dir.doc に **dir** の出力を記録するには、次のように入力します。

```
dir > \records\dir.doc
```

dir.doc が存在しない場合は、**レコード**のディレクトリが存在しない限り、 **dir**によって作成されます。 その場合、次のメッセージが表示されます。

```
File creation error
```

ドライブ C のすべてのディレクトリに拡張子 .txt が付いたすべてのファイル名の一覧を表示するには、次のように入力します。

```
dir c:\*.txt /w/o/s/p
```

**Dir**コマンドは、各ディレクトリ内の一致するファイル名のアルファベット順の一覧を、ワイド形式で表示し、任意のキーを押して続行するまで画面がいっぱいになるたびに一時停止します。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
