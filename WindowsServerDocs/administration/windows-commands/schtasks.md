---
title: schtasks コマンド
description: コマンドとプログラムを定期的または特定の時刻に実行するようにスケジュールを設定し、スケジュールに基づいてタスクを追加および削除し、必要に応じてタスクを開始および停止し、スケジュールされたタスクを表示および変更する schtasks コマンドの参照記事。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 09/16/2020
ms.openlocfilehash: 50b0bd7f7a55a7aa5889c39e4bf9f4e582af7f3b
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388638"
---
# <a name="schtasks-commands"></a>schtasks コマンド

定期的または特定の時刻に実行されるコマンドとプログラムをスケジュールし、スケジュールに基づいてタスクを追加および削除し、必要に応じてタスクを開始および停止して、スケジュールされたタスクを表示および変更します。

> [!NOTE]
> **schtasks.exe**ツールは、**コントロールパネル**のスケジュールされた**タスク**と同じ操作を実行します。 まとめてと同じ意味では、これらのツールを使用できます。

## <a name="required-permissions"></a>必要なアクセス許可

- ローカルコンピューター上のすべてのタスクをスケジュール、表示、および変更するには、Administrators グループのメンバーである必要があります。

- リモートコンピューター上のすべてのタスクをスケジュール、表示、および変更するには、リモートコンピューターの Administrators グループのメンバーであるか、または **/u** パラメーターを使用してリモートコンピューターの管理者の資格情報を指定する必要があります。

- ローカルコンピューターとリモートコンピューターが同じドメインにある場合、またはローカルコンピューターがリモートコンピューターのドメインが信頼するドメインにある場合は、 **/create**または **/change**操作で **/u**パラメーターを使用できます。 そうしないと、リモートコンピューターは指定されたユーザーアカウントを認証できず、アカウントが Administrators グループのメンバーであることを確認できません。

- 実行する予定のタスクには、適切なアクセス許可が必要です。これらのアクセス許可は、タスクによって異なります。 ローカル コンピューターの現在のユーザーのアクセス許可を持つまたはによって指定されたユーザーのアクセス許可を持つ既定では、タスクを実行、 **/u** パラメーターを 1 つが含まれる場合。 o 別のユーザーアカウントのアクセス許可またはシステムアクセス許可を持つタスクを実行する場合は、 **/ru** パラメーターを使用します。

## <a name="syntax"></a>構文

```
schtasks change
schtasks create
schtasks delete
schtasks end
schtasks query
schtasks run
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| [schtasks を変更します。](schtasks-change.md) | タスクの次の1つ以上のプロパティを変更します。<ul><li>タスクが実行するプログラム (/tr)</li><li>タスクを実行するユーザーアカウント (/ru)</li><li>ユーザーアカウントのパスワード (/rp)</li><li>対話型専用のプロパティをタスク (/it) に追加します。</li></ul> |
| [schtasks を作成します。](schtasks-create.md) | 新しいタスクをスケジュールします。|
| [schtasks を削除します。](schtasks-delete.md) | スケジュールされたタスクを削除します。 |
| [schtasks 終了](schtasks-end.md) | タスクによって起動されたプログラムを停止します。 |
| [schtasks クエリ](schtasks-query.md) | コンピューター上で実行するスケジュールされたタスクを表示します。 |
| [schtasks を実行します。](schtasks-run.md) | スケジュールされたタスクを直ちに開始します。 **実行** 操作は、スケジュールは無視されますが、すぐにタスクを実行するプログラム ファイルの場所、ユーザー アカウントおよびタスクに保存されているパスワードを使用します。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
