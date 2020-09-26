---
title: schtasks を削除します。
description: スケジュールによってスケジュールされたタスクを削除する、schtasks delete コマンドの参照記事。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 09/16/2020
ms.openlocfilehash: a5b090ac9520aeae5e603e0c47c0c225b8bd0eff
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91390767"
---
# <a name="schtasks-delete"></a>schtasks を削除します。

スケジュールによってスケジュールされたタスクを削除します。 このコマンドでは、タスクが実行するプログラムや実行中のプログラムを削除することはありません。

## <a name="syntax"></a>構文

```
schtasks /delete /tn {<taskname> | *} [/f] [/s <computer> [/u [<domain>\]<user> [/p <password>]]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /tn `{<taskname> | *}` | 削除するタスクを識別します。 を使用する場合 `*` 、このコマンドは、現在のユーザーによってスケジュールされたタスクだけでなく、コンピューターに対してスケジュールされているすべてのタスクを削除します。 |
| /f | 確認メッセージを抑制します。 タスクは警告なしに削除されます。 |
| /s `<computer>` | (または円記号なし) の名前またはリモート コンピューターの IP アドレスを指定します。 既定値はローカル コンピューターです。 |
| /u `[<domain>]` | 指定したユーザー アカウントのアクセス許可を持つには、このコマンドを実行します。 既定では、コマンドは、ローカル コンピューターの現在のユーザーの権限で実行されます。 指定したユーザー アカウントは、リモート コンピューターの Administrators グループのメンバーである必要があります。 **/U** と **/p** パラメーターが有効に使用する場合のみ **/s**します。 |
| /p `<password>` | 指定されたユーザー アカウントのパスワードを指定、 **/u** パラメーター。 **/P**パラメーターまたは password 引数を指定せずに **/u**パラメーターを使用すると、schtasks はパスワードの入力を求められます。 **/U** と **/p** パラメーターが有効に使用する場合のみ **/s**します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

リモートコンピューターのスケジュールから *メールの開始* タスクを削除するには

```
schtasks /delete /tn Start Mail /s Svr16
```

このコマンドは、 **/s** パラメーターを使用してリモートコンピューターを識別します。

他のユーザーによってスケジュールされたタスクを含め、すべてのタスクをローカルコンピューターのスケジュールから削除すること。

```
schtasks /delete /tn * /f
```

このコマンドは、 **/tn &#42;** パラメーターを使用してコンピューター上のすべてのタスクを表し、 **/f** パラメーターを使用して確認メッセージを非表示にします。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [schtasks 変更コマンド](schtasks-change.md)

- [schtasks create コマンド](schtasks-create.md)

- [schtasks 終了コマンド](schtasks-end.md)

- [schtasks クエリコマンド](schtasks-query.md)

- [schtasks コマンドの実行](schtasks-run.md)
