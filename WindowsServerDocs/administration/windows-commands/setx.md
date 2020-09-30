---
title: setx
description: ユーザーまたはシステム環境で環境変数を作成または変更する setx コマンドの参照記事。プログラミングやスクリプト作成は必要ありません。
ms.topic: reference
ms.assetid: ef37482f-f8a8-4765-951a-2518faac3f44
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 417a00dbb037c298784df81f9c5ed5e9c28485f8
ms.sourcegitcommit: 881a5bd40026288afbcee5fdbf602fd55f833d47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2020
ms.locfileid: "91586442"
---
# <a name="setx"></a>setx

作成するか、プログラミングやスクリプトを必要とせず、ユーザーまたはシステム環境で環境変数を変更します。 **Setx** コマンドは、また、レジストリ キーの値を取得し、テキスト ファイルに書き込みます。

> [!NOTE]
> このコマンドは、システム環境の値を直接および永続的に設定するためのコマンドラインまたはプログラムによる方法のみを提供します。 システム環境変数を使用して手動で構成できます **コントロール パネルの [** またはレジストリ エディターを使用します。 **設定** コマンド インタープリター (Cmd.exe) の内部では、コマンドが現在のコンソール ウィンドウのみのユーザー環境変数を設定します。

## <a name="syntax"></a>構文

```
setx [/s <computer> [/u [<domain>\]<user name> [/p [<password>]]]] <variable> <value> [/m]
setx [/s <computer> [/u [<domain>\]<user name> [/p [<password>]]]] <variable>] /k <path> [/m]
setx [/s <computer> [/u [<domain>\]<user name> [/p [<password>]]]] /f <filename> {[<variable>] {/a <X>,<Y> | /r <X>,<Y> <String>} [/m] | /x} [/d <delimiters>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /s `<computer>` | 名前またはリモート コンピューターの IP アドレスを指定します。 円記号を使用しないでください。 既定値は、ローカル コンピューターの名前です。 |
| /u `[<domain>\]<user name>` | 指定したユーザー アカウントの資格情報でスクリプトを実行します。 既定値は、システムのアクセス許可です。 |
| /p [`<password>`]| 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| `<variable>` | 設定する環境変数の名前を指定します。 |
| `<value>` | 環境変数を設定する値を指定します。 |
| /k `<path>` | 変数のベースをレジストリ キーの情報に設定されるように指定します。 この *パス* では、という構文を使用し `\\<HIVE>\<KEY>\...\<Value>` ます。 たとえば、次のようなパスを指定することができます。 `HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation\StandardName` |
| /f `<filename>` | 使用するファイルを指定します。 |
| /a `<X>,<Y>` | 検索パラメーターとして、絶対座標およびオフセットを指定します。 |
| r `<X>,<Y> <String>` | 相対座標とからのオフセットを指定 **文字列** としてパラメーターを検索します。 |
| /m | システムの環境での変数の設定を指定します。 既定の設定は、ローカルの環境です。 |
| /x | ファイルを無視して、座標が表示されます、 **/a**, 、**/r**, 、および **/d** コマンド ライン オプションです。 |
| d `<delimiters>` | **などの**区切り記号を指定します。また、 **\\** 4 つの組み込みの区切り記号 (スペース、タブ、ENTER、およびラインフィード) に加えて使用することもできます。 有効な区切り記号には、ASCII 文字が含まれます。 区切り文字の最大数は、15、組み込みの区切り記号を含みます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- このコマンドは、UNIX ユーティリティ SETENV に似ています。

- このコマンドを使用すると、コマンドラインモード、レジストリモード、またはファイルモードの3つのソースのいずれかから、ユーザー環境変数とシステム環境変数の値を設定できます。

- このコマンドは、レジストリのマスター環境に変数を書き込みます。 変数の設定と **setx** 変数が現在のコマンド ウィンドウのみで使用できるも現在のコマンド ウィンドウにします。

- **HKEY_CURRENT_USER** と **HKEY_LOCAL_MACHINE** 、唯一サポートされているレジストリ ハイブです。 REG_DWORD、REG_EXPAND_SZ、REG_SZ および REG_MULTI_SZ は、有効な **RegKey** データ型。

- レジストリ内の **REG_MULTI_SZ** 値にアクセスできる場合は、最初の項目のみが抽出され、使用されます。

- このコマンドを使用して、ローカルまたはシステム環境に追加された値を削除することはできません。 このコマンドを変数名と共に使用して、ローカル環境から対応する値を削除することはできません。

- REG_DWORD レジストリ値が抽出され、16 進数のモードで使用します。

- ライン フィード (CRLF) のテキスト ファイルだけをファイルのモードは、キャリッジ リターンの解析をサポートします。

- 既存の変数に対してこのコマンドを実行すると、変数参照が削除され、展開された値が使用されます。

  たとえば、変数% PATH% に% JAVADIR% への参照が含まれていて、% PATH% が **setx**を使用して操作されている場合、% JAVADIR% が展開され、その値がターゲット変数% path% に直接割り当てられます。 これは、% JAVADIR% の今後の更新が% PATH% 変数に反映され **ない** ことを意味します。

- **Setx**を使用して変数にコンテンツを割り当てる場合、1024文字の制限があることに注意してください。

  これは、1024文字を超えた場合にコンテンツがトリミングされ、トリミングされたテキストが対象の変数に適用されることを意味します。 このトリミングテキストが既存の変数に適用されている場合は、対象の変数によって以前に保持されていたデータが失われる可能性があります。

## <a name="examples"></a>例

ローカル環境の *マシン* 環境変数を *Brand1*値に設定するには、次のように入力します。

```
setx MACHINE Brand1
```

システム環境で *コンピューター* 環境変数を *Brand1 Computer*値に設定するには、次のように入力します。

```
setx MACHINE Brand1 Computer /m
```

*Path*環境変数で定義された検索パスを使用するようにローカル環境で*MYPATH*環境変数を設定するには、次のように入力します。

```
setx MYPATH %PATH%
```

をに置き換えた後、 *path*環境変数で定義された検索パスを使用するようにローカル環境の*MYPATH*環境変数を設定するには **~** **%** 、次のように入力します。

```
setx MYPATH ~PATH~
```

*Computer1*という名前のリモートコンピューターでローカル環境の*マシン*環境変数を*Brand1*に設定するには、次のように入力します。

```
setx /s computer1 /u maindom\hiropln /p p@ssW23 MACHINE Brand1
```

*Computer1*という名前のリモートコンピューターの*path*環境変数で定義されている検索パスを使用するようにローカル環境で*MYPATH*環境変数を設定するには、次のように入力します。

```
setx /s computer1 /u maindom\hiropln /p p@ssW23 MYPATH %PATH%
```

ローカル環境の *Tzone* 環境変数を **HKEY_LOCAL_MACHINE \system\currentcontrolset\control\timezoneinformation\standardname** レジストリキーの値に設定するには、次のように入力します。

```
setx TZONE /k HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation\StandardName
```

*Computer1*という名前のリモートコンピューターのローカル環境で*tzone*環境変数を、 **HKEY_LOCAL_MACHINE \system\currentcontrolset\control\timezoneinformation\standardname**レジストリキーの値に設定するには、次のように入力します。

```
setx /s computer1 /u maindom\hiropln /p p@ssW23 TZONE /k HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation\StandardName
```

システム環境の *ビルド* 環境変数を **HKEY_LOCAL_MACHINE \software\microsoft\windowsnt\currentversion\currentbuildnumber** レジストリキーの値に設定するには、次のように入力します。

```
setx BUILD /k HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\CurrentVersion\CurrentBuildNumber /m
```

Computer1 をという名前の値をリモート コンピューターのシステムの環境でビルドの環境変数を設定する、 **HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\CurrentVersion\CurrentBuildNumber** レジストリ キーの型。

```
setx /s computer1 /u maindom\hiropln /p p@ssW23  BUILD /k HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\CurrentBuildNumber /m
```

内容の対応する座標と共に、 *Ipconfig*という名前のファイルの内容を表示するには、次のように入力します。

```
setx /f ipconfig.out /x
```

ローカル環境で*Ipaddr*環境変数を設定するには、 *Ipconfig* *ファイルで、* 次のように入力します。

```
setx IPADDR /f ipconfig.out /a 5,11
```

ローカル環境の*OCTET1*環境変数を、区切り文字 **# $ *** を持つ*Ipconfig*ファイル内の座標*5、3*の値に設定するには、次のように入力します。

```
setx OCTET1 /f ipconfig.out /a 5,3 /d #$*.
```

ローカル環境で*Ipgateway*環境変数を設定するには、次のように入力し*ます。* この値は、Ipconfig ファイル内の*ゲートウェイ*の座標に関して、座標*0, 7*にあります。

```
setx IPGATEWAY /f ipconfig.out /r 0,7 Gateway
```

*Computer1*という名前のコンピューターに、内容の対応する座標と共に*Ipconfig*ファイルの内容を表示するには、次のように入力します。

```
setx /s computer1 /u maindom\hiropln /p p@ssW23 /f ipconfig.out /x
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
