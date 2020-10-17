---
title: tlntadmn
description: ローカルコンピューターまたはリモートコンピューターを管理し、telnet サーバーサービスを実行している tlntの管理 n コマンドの参照記事。
ms.topic: reference
ms.assetid: 78b61e8d-b953-44bb-8d57-f3b42da9e7a8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9a4de6903d5a9979f45677176d023c694e20cdfd
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156441"
---
# <a name="tlntadmn"></a>tlntadmn

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Telnet サーバーサービスを実行しているローカルコンピューターまたはリモートコンピューターを管理します。 パラメーターを指定せずに使用した場合、 **tlntて** いる現在のサーバー設定が表示されます。

このコマンドを実行するには、管理者資格情報を使用してローカルコンピューターにログオンする必要があります。 リモートコンピューターを管理するには、リモートコンピューターの管理者資格情報も指定する必要があります。 これを行うには、ローカルコンピューターとリモートコンピューターの両方の管理者資格情報を持つアカウントを使用してローカルコンピューターにログオンします。 この方法を使用できない場合は、 **-u** パラメーターと **-p** パラメーターを使用して、リモートコンピューターの管理者資格情報を指定できます。

## <a name="syntax"></a>構文

```
tlntadmn [<computername>] [-u <username>] [-p <password>] [{start | stop | pause | continue}] [-s {<sessionID> | all}] [-k {<sessionID> | all}] [-m {<sessionID> | all}  <message>] [config [dom = <domain>] [ctrlakeymap = {yes | no}] [timeout = <hh>:<mm>:<ss>] [timeoutactive = {yes | no}] [maxfail = <attempts>] [maxconn = <connections>] [port = <number>] [sec {+ | -}NTLM {+ | -}passwd] [mode = {console | stream}]] [-?]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<computername>` | 接続先のサーバーの名前を指定します。 既定値はローカル コンピューターです。 |
| -u `<username> -p <password>` | 管理するリモートサーバーの管理者資格情報を指定します。 このパラメーターは、管理者資格情報でログオンしていないリモートサーバーを管理する場合に必要です。 |
| start | telnet サーバーサービスを開始します。 |
| stop | Telnet サーバーサービスを停止します。 |
| pause | Telnet サーバーサービスを一時停止します。 新しい接続は受け付けられません。 |
| continue | Telnet サーバーサービスを再開します。 |
| -s `{<sessionID> | all}` | アクティブな telnet セッションを表示します。 |
| -k `{<sessionID> | all}` | Telnet セッションを終了します。 セッション ID を入力して特定のセッションを終了するか、[すべて] を入力してすべてのセッションを終了します。 |
| -m `{<sessionID> | all}  <message>` | 1つ以上のセッションにメッセージを送信します。 セッション ID を入力して特定のセッションにメッセージを送信するか、[すべて] を入力してすべてのセッションにメッセージを送信します。 引用符で囲んで送信するメッセージを入力します。 |
| config dom = `<domain>` | サーバーの既定のドメインを構成します。 |
| 構成 ctrlakeymap マップ = `{yes | no}` | Telnet サーバーが CTRL + A を ALT として解釈するかどうかを指定します。 ショートカットキーをマップするには **「yes」** と入力し、マッピングを禁止するには「 **no** 」と入力します。 |
| 構成のタイムアウト = `<hh>:<mm>:<ss>` | タイムアウト期間を時間、分、および秒で設定します。 |
| 構成 timeoutactive = `{yes | no}` | アイドル状態のセッションのタイムアウトを有効にします。 |
| 構成 maxfail = `<attempts>` | 切断するまでのログオン失敗回数の最大値を設定します。 |
| 構成 maxconn = `<connections>` | 接続の最大数を設定します。 |
| 構成ポート = `<number>` | Telnet ポートを設定します。 1024より小さい整数値を指定してポートを指定する必要があります。 |
| 構成秒 `{+ | -}NTLM {+ | -}passwd` | ログオン試行を認証するために NTLM とパスワードのどちらを使用するか、またはその両方を使用するかを指定します。 特定の種類の認証を使用するには、 **+** その認証の種類の前にプラス記号 () を入力します。 特定の種類の認証を使用しないようにするには、 **-** その認証の種類の前にマイナス記号 () を入力します。 |
| 構成モード = `{console | stream}` | 操作のモードを指定します。 |
| -? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>使用例

アイドルセッションタイムアウトを30分に構成するには、次のように入力します。

```
tlntadmn config timeout=0:30:0
```

アクティブな telnet セッションを表示するには、次のように入力します。

```
tlntadmn -s
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [telnet 操作ガイド](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753164(v=ws.10))
