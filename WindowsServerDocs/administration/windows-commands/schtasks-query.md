---
title: schtasks クエリ
description: コンピューターで実行するようにスケジュールされているすべてのタスクを一覧表示する、schtasks クエリコマンドの参照記事です。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 09/16/2020
ms.openlocfilehash: c1bff666f762b21e8dbcf2bff59383d49cab6409
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91390746"
---
# <a name="schtasks-query"></a>schtasks クエリ

コンピューター上で実行するようにスケジュールされているすべてのタスクを一覧表示します。

構文

```
schtasks [/query] [/fo {TABLE | LIST | CSV}] [/nh] [/v] [/s <computer> [/u [<domain>\]<user> [/p <password>]]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /query | 必要に応じて、操作の名前を指定します。 パラメーターを指定せずにこのクエリを実行すると、クエリが実行します。 |
| /fo `<format>` | 出力形式を指定します。 有効な値は、 *TABLE*、 *LIST*、または *CSV*です。 |
| /nh | テーブル表示から列見出しを削除します。 このパラメーターは、 *テーブル* または *CSV* の出力形式で有効です。 |
| /v | タスクの詳細プロパティを表示に追加します。 このパラメーターは、 *リスト* または *CSV* の出力形式で有効です。 |
| /s `<computer>` | (または円記号なし) の名前またはリモート コンピューターの IP アドレスを指定します。 既定値はローカル コンピューターです。 |
| /u `[<domain>]` | 指定したユーザー アカウントのアクセス許可を持つには、このコマンドを実行します。 既定では、コマンドは、ローカル コンピューターの現在のユーザーの権限で実行されます。 指定したユーザー アカウントは、リモート コンピューターの Administrators グループのメンバーである必要があります。 **/U** と **/p** パラメーターが有効に使用する場合のみ **/s**します。 |
| /p `<password>` | 指定されたユーザー アカウントのパスワードを指定、 **/u** パラメーター。 **/P**パラメーターまたは password 引数を指定せずに **/u**パラメーターを使用すると、schtasks はパスワードの入力を求められます。 **/U** と **/p** パラメーターが有効に使用する場合のみ **/s**します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

ローカルコンピューターにスケジュールされているすべてのタスクを一覧表示するには、次のように入力します。

```
schtasks
schtasks /query
```

これらのコマンドは、結果は同じされ、同じ意味で使用できます。

ローカルコンピューター上のタスクの詳細表示を要求するには、次のように入力します。

```
schtasks /query /fo LIST /v
```

このコマンドは、 **/v** パラメーターを使用して詳細な (verbose) display を要求し、 **/fo list** パラメーターを使用して、表示を読みやすくするための一覧として書式設定します。 このコマンドを使用すると、作成したタスクが意図した定期的なパターンであることを確認します。

リモートコンピューターにスケジュールされたタスクの一覧を要求し、ローカルコンピューター上のコンマ区切りのログファイルにタスクを追加するには、次のように入力します。

```
schtasks /query /s Reskit16 /fo csv /nh >> \\svr01\data\tasklogs\p0102.csv
```

このコマンド形式を使用して、収集し、複数のコンピューターにスケジュールされているタスクを追跡することができます。 このコマンドは、 **/s** パラメーターを使用してリモートコンピューターを識別し、 *Reskit16*、 **/fo** パラメーターを使用して形式を指定し、 **/nh** パラメーターを使用して列見出しを非表示にします。 **>>** 追加シンボルは、ローカルコンピューター *Svr01*上のタスクログ*p0102.csv*に出力をリダイレクトします。 リモート コンピューターでコマンドを実行しているために、ローカル コンピューターのパスは完全修飾する必要があります。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [schtasks 変更コマンド](schtasks-change.md)

- [schtasks create コマンド](schtasks-create.md)

- [schtasks delete コマンド](schtasks-delete.md)

- [schtasks 終了コマンド](schtasks-end.md)

- [schtasks コマンドの実行](schtasks-run.md)