---
title: eventcreate
description: Eventcreate コマンドの参照記事。管理者は、指定されたイベントログにカスタムイベントを作成できます。
ms.topic: reference
ms.assetid: f2b1b26d-a70e-49a6-832b-91eb5a1a159a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d2fa1e4a90d0c24138c5353c5cf1b22308204d6f
ms.sourcegitcommit: 0b3d6661c44aa1a697087e644437279142726d84
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/15/2020
ms.locfileid: "90083653"
---
# <a name="eventcreate"></a>eventcreate

管理者が、指定されたイベントログにカスタムイベントを作成できるようにします。

> [!IMPORTANT]
> カスタムイベントをセキュリティログに書き込むことはできません。

## <a name="syntax"></a>構文

```
eventcreate [/s <computer> [/u <domain\user> [/p <password>]] {[/l {APPLICATION|SYSTEM}]|[/so <srcname>]} /t {ERROR|WARNING|INFORMATION|SUCCESSAUDIT|FAILUREAUDIT} /id <eventID> /d <description>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- |------------ |
| /s `<computer>` | 名前またはリモート コンピューターの IP アドレスを指定します (円記号を使用しない)。 既定値はローカル コンピューターです。 |
| /u `<domain\user>` | またはによって指定されたユーザーのアカウントアクセス許可を使用してコマンドを実行し `<user>` `<domain\user>` ます。 既定値は、コマンドを実行しているコンピューターの現在のログオンユーザーのアクセス許可です。 |
| /p `<password>` | 指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。 |
| /l `{APPLICATION | SYSTEM}` | イベントが作成されるイベントログの名前を指定します。 有効なログ名は、 **アプリケーション** または **システム**です。 |
| /so `<srcname>` | イベントに使用するソースを指定します。 有効なソースは任意の文字列にすることができ、イベントを生成しているアプリケーションまたはコンポーネントを表す必要があります。 |
| /t `{ERROR | WARNING | INFORMATION | SUCCESSAUDIT | FAILUREAUDIT}` | 作成するイベントの種類を指定します。 有効な種類は、 **ERROR**、 **WARNING**、 **INFORMATION**、 **SUCCESSAUDIT**、および **failureaudit**です。 |
| /id `<eventID>` | イベントのイベント ID を指定します。 有効な ID は、1 ~ 1000 の任意の数です。 |
| d `<description>` | 新しく作成されたイベントに使用する説明を指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

次の例は、 **eventcreate** コマンドを使用する方法を示しています。

```
eventcreate /t ERROR /id 100 /l application /d "Create event in application log"
eventcreate /t INFORMATION /id 1000 /d "Create event in WinMgmt source"
eventcreate /t ERROR /id 201 /so winword /l application /d "New src Winword in application log"
eventcreate /s server /t ERROR /id 100 /l application /d "Remote machine without user credentials"
eventcreate /s server /u user /p password /id 100 /t ERROR /l application /d "Remote machine with user credentials"
eventcreate /s server1 /s server2 /u user /p password /id 100 /t ERROR /d "Creating events on Multiple remote machines"
eventcreate /s server /u user /id 100 /t WARNING /d "Remote machine with partial user credentials"
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
