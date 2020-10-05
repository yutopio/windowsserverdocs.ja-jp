---
title: tasklist
description: Tasklist コマンドの参照記事。ローカルコンピューターまたはリモートコンピューターで実行されているプロセスの一覧を表示します。
ms.topic: reference
ms.assetid: 8dbe30ee-1484-46be-917b-5ca3ff4fdc9c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: af89112d98cb7799a2fa910d562ac8c2a35bba19
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718059"
---
# <a name="tasklist"></a>tasklist

ローカル コンピューターまたはリモート コンピューター上で現在実行中のプロセスの一覧を表示します。 **Tasklist** 置き換えます、 **tlist** ツールです。

> [!NOTE]
> このコマンドは、 **tlist.exe** ツールを置き換えます。

## <a name="syntax"></a>構文

```
tasklist [/s <computer> [/u [<domain>\]<username> [/p <password>]]] [{/m <module> | /svc | /v}] [/fo {table | list | csv}] [/nh] [/fi <filter> [/fi <filter> [ ... ]]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /s `<computer>` | 名前またはリモート コンピューターの IP アドレスを指定します (円記号を使用しない)。 既定値はローカル コンピューターです。 |
| /u `<domain>\<username>` | またはによって指定されたユーザーのアカウントアクセス許可を使用してコマンドを実行し `<username>` `<domain>\<username>` ます。 **/U**パラメーターは、 **/s**も指定されている場合にのみ指定できます。 既定では、コマンドを発行しているコンピューターに現在ログオンしているユーザーのアクセス許可です。 |
| /p `<password>` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| /m `<module>` | 読み込まれた DLL モジュールを指定したパターンの名前に一致するすべてのタスクを一覧表示します。 モジュール名が指定されていない場合、このオプションは、各タスクによって読み込まれたすべてのモジュールを表示します。 |
| svc | 切り捨てることがなく、各プロセスのすべてのサービス情報を一覧表示します。 有効な場合に、 **/fo** にパラメーターが設定されている **テーブル**します。 |
| /v | 出力に詳細なタスクの情報を表示します。 切り捨てることがなく完全な詳細な出力を使用して **/v** と **/svc** 化します。 |
| /fo `{table | list | csv}` | 使用して、出力形式を指定します。 有効な値は **テーブル**, 、**リスト**, 、および **csv**します。 出力の既定の形式は **table**です。 |
| /nh | 出力に列ヘッダーを抑制します。 **/Fo**パラメーターが**table**または**csv**に設定されている場合に有効です。 |
| /fi `<filter>` | 含めることも、クエリから除外するプロセスの種類を指定します。 1 つ以上のフィルターを使用するか、ワイルドカード文字を使用して (`\`) イメージ名をすべてのタスクを指定します。 有効なフィルターの一覧については、この記事の「 **フィルター名、演算子、および値** 」を参照してください。  |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="filter-names-operators-and-values"></a>フィルター名、演算子、および値

| フィルター名 | 有効な演算子 | 有効な値 |
|--|--|--|
| 状態 | eq、ne | `RUNNING | NOT RESPONDING | UNKNOWN`. リモートシステムを指定した場合、このフィルターはサポートされません。 |
| IMAGENAME | eq、ne | イメージ名 |
| PID | eq、ne、gt、lt、ge、le | PID 値 |
| SESSION | eq、ne、gt、lt、ge、le | セッション番号 |
| セッション名 | eq、ne | [セッション名] |
| CPUtime | eq、ne、gt、lt、ge、le | CPU 時間を *HH: MM: ss*の形式で指定します。ここで、 *mm* と *SS* は 0 ~ 59 の間、 *HH* は符号なしの数値です。 |
| MEMUSAGE | eq、ne、gt、lt、ge、le | メモリの使用量 (KB 単位) |
| USERNAME | eq、ne | 任意の有効なユーザー名 ( `<user>` または `<domain\user>` ) |
| サービス | eq、ne | サービス名 |
| WINDOWTITLE | eq、ne | ウィンドウのタイトル。 リモートシステムを指定した場合、このフィルターはサポートされません。 |
| モジュール | eq、ne | DLL 名 |

## <a name="examples"></a>例

*プロセス ID が1000より大きい*すべてのタスクを一覧表示し、 *csv 形式で表示*するには、次のように入力します。

```
tasklist /v /fi "PID gt 1000" /fo csv
```

現在実行されているシステム プロセスを一覧表示するには、次のように入力します。

```
tasklist /fi "USERNAME ne NT AUTHORITY\SYSTEM" /fi "STATUS eq running"
```

現在実行されているすべてのプロセスの詳細情報を一覧表示するには、次のように入力します。

```
tasklist /v /fi "STATUS eq running"
```

リモートコンピューターの *srvmain*にあるプロセスのすべてのサービス情報を一覧表示するには、次のように *入力します*。

```
tasklist /s srvmain /svc /fi "MODULES eq ntdll*"
```

リモートコンピューターの *srvmain*のプロセスを一覧表示するには、現在ログオンしているユーザーアカウントの資格情報を使用して、次のように入力します。

```
tasklist /s srvmain
```

リモートコンピューターの *srvmain*のプロセスを一覧表示するには、 *ユーザーアカウント Hiropln*の資格情報を使用し、次のように入力します。

```
tasklist /s srvmain /u maindom\hiropln /p p@ssW23
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
