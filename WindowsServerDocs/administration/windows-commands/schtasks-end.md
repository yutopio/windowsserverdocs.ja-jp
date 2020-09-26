---
title: schtasks 終了
description: スケジュールされたタスクによって開始されたプログラムのインスタンスのみを停止する、schtasks end コマンドの参照記事。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 09/16/2020
ms.openlocfilehash: 7075c8689a39c7bc9eba917298678977916e29fa
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91390751"
---
# <a name="schtasks-end"></a>schtasks 終了

スケジュールされたタスクによって開始されたプログラムのインスタンスだけを停止します。 他のプロセスを停止するには、 [TaskKill](taskkill.md) コマンドを使用する必要があります。

## <a name="syntax"></a>構文

```
schtasks /end /tn <taskname> [/s <computer> [/u [<domain>\]<user> [/p <password>]]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /tn `<taskname>` | プログラムを起動したタスクを識別します。 このパラメーターは必須です。 |
| /s `<computer>` | (または円記号なし) の名前またはリモート コンピューターの IP アドレスを指定します。 既定値はローカル コンピューターです。 |
| /u `[<domain>]` | 指定したユーザー アカウントのアクセス許可を持つには、このコマンドを実行します。 既定では、コマンドは、ローカル コンピューターの現在のユーザーの権限で実行されます。 指定したユーザー アカウントは、リモート コンピューターの Administrators グループのメンバーである必要があります。 **/U** と **/p** パラメーターが有効に使用する場合のみ **/s**します。 |
| /p `<password>` | 指定されたユーザー アカウントのパスワードを指定、 **/u** パラメーター。 **/P**パラメーターまたは password 引数を指定せずに **/u**パラメーターを使用すると、schtasks はパスワードの入力を求められます。 **/U** と **/p** パラメーターが有効に使用する場合のみ **/s**します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

*メモ帳*タスクによって開始された Notepad.exe のインスタンスを停止するには、次のように入力します。

```
schtasks /end /tn "My Notepad"
```

リモートコンピューター上の *interneton* タスクによって開始された Internet Explorer のインスタンスを停止するには、 *Svr01*、次のように入力します。

```
schtasks /end /tn InternetOn /s Svr01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [schtasks 変更コマンド](schtasks-change.md)

- [schtasks create コマンド](schtasks-create.md)

- [schtasks delete コマンド](schtasks-delete.md)

- [schtasks クエリコマンド](schtasks-query.md)

- [schtasks コマンドの実行](schtasks-run.md)