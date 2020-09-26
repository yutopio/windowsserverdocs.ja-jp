---
title: schtasks を実行します。
description: Schtasks run コマンドの参照記事。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 09/16/2020
ms.openlocfilehash: 9304e41c21899ce49bd6d4d4409ae3b47d3746aa
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91390743"
---
# <a name="schtasks-run"></a>schtasks を実行します。

スケジュールされたタスクを直ちに開始します。 実行 操作は、スケジュールは無視されますが、すぐにタスクを実行するプログラム ファイルの場所、ユーザー アカウントおよびタスクに保存されているパスワードを使用します。 タスクを実行するタスクのスケジュールは影響しないため、タスクのスケジュールされた次回の実行を変更することはできません。

## <a name="syntax"></a>構文

```
schtasks /run /tn <taskname> [/s <computer> [/u [<domain>\]<user> [/p <password>]]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /tn `<taskname>` | 開始するタスクを識別します。 このパラメーターは必須です。 |
| /s `<computer>` | (または円記号なし) の名前またはリモート コンピューターの IP アドレスを指定します。 既定値はローカル コンピューターです。 |
| /u `[<domain>]` | 指定したユーザー アカウントのアクセス許可を持つには、このコマンドを実行します。 既定では、コマンドは、ローカル コンピューターの現在のユーザーの権限で実行されます。 指定したユーザー アカウントは、リモート コンピューターの Administrators グループのメンバーである必要があります。 **/U** と **/p** パラメーターが有効に使用する場合のみ **/s**します。 |
| /p `<password>` | 指定されたユーザー アカウントのパスワードを指定、 **/u** パラメーター。 **/P**パラメーターまたは password 引数を指定せずに **/u**パラメーターを使用すると、schtasks はパスワードの入力を求められます。 **/U** と **/p** パラメーターが有効に使用する場合のみ **/s**します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- この操作を使用すると、タスクをテストできます。 タスクが実行されない場合は、タスクスケジューラサービスのトランザクションログでエラーを確認し `<Systemroot>\SchedLgU.txt` ます。

- リモートでのタスクを実行するには、リモート コンピューターでタスクをスケジュールする必要があります。 タスクを実行すると、リモートコンピューター上でのみ実行されます。 タスクがリモートコンピューター上で実行されていることを確認するには、タスクマネージャーまたはタスクスケジューラサービスのトランザクションログを使用し `<Systemroot>\SchedLgU.txt` ます。

## <a name="examples"></a>例

*セキュリティスクリプト*タスクを開始するには、次のように入力します。

```
schtasks /run /tn Security Script
```

リモートコンピューターで Svr01 の *更新* タスクを開始するには、次のように入力します。

```
schtasks /run /tn Update /s Svr01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [schtasks 変更コマンド](schtasks-change.md)

- [schtasks create コマンド](schtasks-create.md)

- [schtasks delete コマンド](schtasks-delete.md)

- [schtasks 終了コマンド](schtasks-end.md)

- [schtasks クエリコマンド](schtasks-query.md)