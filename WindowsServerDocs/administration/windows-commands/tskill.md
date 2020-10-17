---
title: tskill
description: Tskill コマンドの参照記事。リモートデスクトップセッションホストサーバー上のセッションで実行されているプロセスを終了します。
ms.topic: reference
ms.assetid: 08986e6a-6900-4ece-85a1-8f73b14db1b3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b281df4852bc5fbc0756e7b052d82ea2f9bab6d5
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156379"
---
# <a name="tskill"></a>tskill

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートデスクトップセッションホストサーバー上のセッションで実行されているプロセスを終了します。

> [!NOTE]
> このコマンドを使用すると、管理者でない限り、自分に属しているプロセスのみを終了できます。 管理者は、すべての **tskill** 関数にフルアクセスでき、他のユーザーセッションで実行されているプロセスを終了できます。
>
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
tskill {<processID> | <processname>} [/server:<servername>] [/id:<sessionID> | /a] [/v]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<processID>` | 終了するプロセスの ID を指定します。 |
| `<processname>` | 終了するプロセスの名前を指定します。 このパラメーターには、ワイルドカード文字を含めることができます。 |
| /server:`<servername>` | 終了するプロセスを含むターミナルサーバーを指定します。 **/Server**が指定されていない場合は、現在のリモートデスクトップセッションホストサーバーが使用されます。 |
| /id`<sessionID>` | 指定されたセッションで実行されているプロセスを終了します。 |
| /a | すべてのセッションで実行されているプロセスを終了します。 |
| /v | 実行されているアクションに関する情報を表示します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- セッション内で動作しているすべてのプロセスが終了すると、セッションも終了します。

- `<processname>`およびパラメーターを使用する場合 `/server:<servername>` `/id:<sessionID>` は、または **/a**パラメーターも指定する必要があります。

## <a name="examples"></a>使用例

プロセス6543を終了するには、次のように入力します。

```
tskill 6543
```

セッション5で実行されているプロセスエクスプローラーを終了するには、次のように入力します。

```
tskill explorer /id:5
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)
