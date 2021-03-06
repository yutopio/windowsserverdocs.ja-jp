---
title: query session
description: クエリセッションコマンドの参照記事。リモートデスクトップセッションホストサーバー上のセッションに関する情報を表示します。
ms.topic: reference
ms.assetid: abc0ace8-0b74-4b6e-a937-a78bb4b61a1f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2842aa9b0a38438a92ee2b7072b1a1054642fd62
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639888"
---
# <a name="query-session"></a>query session

適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートデスクトップセッションホストサーバー上のセッションに関する情報を表示します。 一覧には、アクティブなセッションだけでなく、サーバーが実行している他のセッションに関する情報も含まれています。

> [!NOTE]
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
query session [<sessionname> | <username> | <sessionID>] [/server:<servername>] [/mode] [/flow] [/connect] [/counter]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<sessionname>` | クエリを実行するセッションの名前を指定します。 |
| `<username>` | クエリを実行するセッションを持つユーザーの名前を指定します。 |
| `<sessionID>` | クエリを実行するセッションの ID を指定します。 |
| /server:`<servername>` | 照会する rd セッションホストサーバーを識別します。 既定値は現在のサーバーです。 |
| /mode | 現在の行の設定を表示します。 |
| フロー (& a) | 現在のフロー制御の設定を表示します。 |
| /connect | 現在の接続設定を表示します。 |
| /counter | 作成、切断、再接続されたセッションの合計数など、現在のカウンター情報が表示されます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- ユーザーは、ユーザーが現在ログオンしているセッションに対していつでもクエリを実行できます。 他のセッションを照会するには、ユーザーに特別なアクセス許可が必要です。

- <*username*> *、<sessions*>、または *sessionID* パラメーターを使用してセッションを指定しない場合、このクエリでは、システム内のすべてのアクティブなセッションに関する情報が表示されます。

- **クエリセッション**で情報が返されると、 `(>)` 現在のセッションの前に不等号が表示されます。 以下に例を示します。

    ```
    C:\>query session
        SESSIONNAME     USERNAME        ID STATE    TYPE    DEVICE
        console         Administrator1  0 active    wdcon
        >rdp-tcp#1      User1           1 active    wdtshare
        rdp-tcp                         2 listen    wdtshare
                                        4 idle
                                        5 idle
    ```

    条件:
  - [セッション名は、セッションに割り当てられた名前**を指定し**ます。
  - **USERNAME** は、セッションに接続されているユーザーのユーザー名を示します。
  - **State** は、セッションの現在の状態に関する情報を提供します。
  - **種類** は、セッションの種類を示します。
  - コンソールまたはネットワークに接続されたセッションには存在しない**デバイス**は、セッションに割り当てられているデバイス名です。
  - 初期状態が無効として構成されているセッションは、有効になるまで **クエリセッション** の一覧に表示されません。

### <a name="examples"></a>例

サーバー *Server2*のすべてのアクティブなセッションに関する情報を表示するには、次のように入力します。

```
query session /server:Server2
```

アクティブなセッションの *modeM02*に関する情報を表示するには、次のように入力します。

```
query session modeM02
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [クエリコマンド](query.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)
