---
title: taskkill
description: 1つ以上のタスクまたはプロセスを終了する、taskkill コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 2b71e792-08b6-46d4-95a5-cb6336a79524
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e022bc980e2acd7fb70bf13af52f8096fd6aaa1f
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718079"
---
# <a name="taskkill"></a>taskkill

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

1 つまたは複数のタスクまたはプロセスを終了します。 プロセス ID またはイメージ名を使用してプロセスを終了できます。 [Tasklist コマンド](tasklist.md)コマンドを使用して、終了するプロセスのプロセス ID (PID) を決定できます。

> [!NOTE]
> このコマンドは、 **kill** ツールを置き換えます。

## <a name="syntax"></a>構文

```
taskkill [/s <computer> [/u [<domain>\]<username> [/p [<password>]]]] {[/fi <filter>] [...] [/pid <processID> | /im <imagename>]} [/f] [/t]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
|  /s `<computer>` | 名前またはリモート コンピューターの IP アドレスを指定します (円記号を使用しない)。 既定値はローカル コンピューターです。 |
| /u `<domain>\<username>` | またはによって指定されたユーザーのアカウントアクセス許可を使用してコマンドを実行し `<username>` `<domain>\<username>` ます。 **/U**パラメーターは、 **/s**も指定されている場合にのみ指定できます。 既定では、コマンドを発行しているコンピューターに現在ログオンしているユーザーのアクセス許可です。 |
| /p `<password>` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| /fi `<filter>` | タスクのセットを選択するフィルターを適用します。 1 つ以上のフィルターを使用するか、ワイルドカード文字を使用して (`*`) イメージ名をすべてのタスクを指定します。 有効なフィルターの一覧については、この記事の「 **フィルター名、演算子、および値** 」を参照してください。 |
| /pid `<processID>` | 終了するプロセスのプロセス ID を指定します。 |
| /im `<imagename>` | 終了するプロセスのイメージの名前を指定します。 ワイルドカード文字を使用して (`*`) をすべてのイメージ名を指定します。 |
| /f | プロセスを強制的に終了することを指定します。 リモートプロセスでは、このパラメーターは無視されます。すべてのリモートプロセスが強制的に終了されます。 |
| /t | 指定したプロセスと、そのプロセスによって開始された子プロセスを終了します。 |

#### <a name="filter-names-operators-and-values"></a>フィルター名、演算子、および値

| フィルター名 | 有効な演算子 | 有効な値 |
|--|--|--|
| 状態 | eq、ne | `RUNNING | NOT RESPONDING | UNKNOWN` |
| IMAGENAME | eq、ne | イメージ名 |
| PID | eq、ne、gt、lt、ge、le | PID 値 |
| SESSION | eq、ne、gt、lt、ge、le | セッション番号 |
| CPUtime | eq、ne、gt、lt、ge、le | CPU 時間を *HH: MM: ss*の形式で指定します。ここで、 *mm* と *SS* は 0 ~ 59 の間、 *HH* は符号なしの数値です。 |
| MEMUSAGE | eq、ne、gt、lt、ge、le | メモリの使用量 (KB 単位) |
| USERNAME | eq、ne | 任意の有効なユーザー名 ( `<user>` または `<domain\user>` ) |
| サービス | eq、ne | サービス名 |
| WINDOWTITLE | eq、ne | ウィンドウのタイトル |
| モジュール | eq、ne | DLL 名 |

## <a name="remarks"></a>解説

- リモートシステムが指定されている場合、 **system.windows.controls.page.windowtitle** と **STATUS** のフィルターはサポートされません。

- ワイルドカード文字 ( `*` ) は、フィルターが適用されている場合にのみ、オプションで受け入れられ `*/im` ます。

- リモートプロセスの終了は、 **/f** オプションが指定されているかどうかに関係なく、常に強制的に実行されます。

- ホスト名フィルターにコンピューター名を指定すると、シャットダウンが発生し、すべてのプロセスが停止します。

## <a name="examples"></a>例

プロセス Id *1230*、 *1241*、および *1253*を使用してプロセスを終了するには、次のように入力します。

```
taskkill /pid 1230 /pid 1241 /pid 1253
```

プロセスを強制的に終了するには、システムによって開始された場合は *Notepad.exe* 次のように入力します。

```
taskkill /f /fi "USERNAME eq NT AUTHORITY\SYSTEM" /im notepad.exe
```

リモートコンピューターの *Srvmain* で、 *メモ*で始まるイメージ名を使用してすべてのプロセスを終了し、ユーザーアカウント *Hiropln*の資格情報を使用するには、次のように入力します。

```
taskkill /s srvmain /u maindom\hiropln /p p@ssW23 /fi "IMAGENAME eq note*" /im *
```

プロセス ID *2134* と開始した子プロセスを終了するには、管理者アカウントによってプロセスが開始された場合にのみ、次のように入力します。

```
taskkill /pid 2134 /t /fi "username eq administrator"
```

イメージ名に関係なく、 *1000*以上のプロセス ID を持つすべてのプロセスを終了するには、次のように入力します。

```
taskkill /f /fi "PID ge 1000" /im *
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [tasklist コマンド](tasklist.md)
