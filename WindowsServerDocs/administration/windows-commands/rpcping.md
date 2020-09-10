---
title: rpcping
description: Rpcping コマンドの参照記事。 Microsoft Exchange Server を実行しているコンピューターと、ネットワーク上でサポートされている Microsoft Exchange クライアントワークステーションの間の RPC 接続を確認します。
ms.topic: reference
ms.assetid: 7382aa0d-90fc-47c0-84b3-15f52dd656d0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7351195d8206cb13b334ca3e06ffb794e4a13461
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641178"
---
# <a name="rpcping"></a>rpcping

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ネットワーク上の Microsoft Exchange Server とサポートされている Microsoft Exchange クライアント ワークステーションのいずれかを実行しているコンピューター間の RPC 接続を確認します。 このユーティリティを使用してをネットワーク経由でクライアント ワークステーションから Microsoft Exchange Server のサービスが RPC 要求に応答しているを確認します。

## <a name="syntax"></a>構文

```
rpcping [/t <protseq>] [/s <server_addr>] [/e <endpoint>
        |/f <interface UUID>[,majorver]] [/O <interface object UUID]
        [/i <#_iterations>] [/u <security_package_id>] [/a <authn_level>]
        [/N <server_princ_name>] [/I <auth_identity>] [/C <capabilities>]
        [/T <identity_tracking>] [/M <impersonation_type>]
        [/S <server_sid>] [/P <proxy_auth_identity>] [/F <RPCHTTP_flags>]
        [/H <RPC/HTTP_authn_schemes>] [/o <binding_options>]
        [/B <server_certificate_subject>] [/b] [/E] [/q] [/c]
        [/A <http_proxy_auth_identity>] [/U <HTTP_proxy_authn_schemes>]
        [/r <report_results_interval>] [/v <verbose_level>] [/d]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /t `<protseq>` | 使用するプロトコルの順序を指定します。 には、標準の RPC プロトコルシーケンス (ncacn_ip_tcp、ncacn_np、または ncacn_http) のいずれかを指定できます。<p>指定しない場合、既定値は ncacn_ip_tcp にします。 |
| /s `<server_addr>` | サーバーのアドレスを指定します。 指定されていない場合は、ローカル コンピューターを ping します。 |
| /e `<endpoint>` | Ping を実行するエンドポイントを指定します。 指定されていない場合は、ターゲット コンピューター上のエンドポイント マッパーが ping されます。<p>このオプションは、インターフェイスと同時に (**/f**) オプション。 |
| /o `<binding_options>` | RPC ping のバインド オプションを指定します。 |
| /f `<interface UUID>[,Majorver]` | Ping を実行するインターフェイスを指定します。 このオプションは、エンドポイント オプションと相互に排他的です。 インターフェイスは、UUID として指定します。<p>*majorver*が指定されていない場合は、インターフェイスのバージョン1が検索されます。<p>インターフェイスを指定すると、 **rpcping** がクエリを指定したインターフェイスのエンドポイントを取得する対象コンピューターにエンドポイント マッパー。 エンドポイント マッパーは、コマンドラインで指定されたオプションを使用して照会されます。 |
| /O `<object UUID>` | インターフェイスには、1 つが登録されている場合は、オブジェクトの UUID を指定します。 |
| /i `<#_iterations>` | 呼び出しの数を指定します。 既定値は 1 です。 このオプションは、複数のイテレーションが指定されている場合は、接続の待機時間を測定するために便利です。 |
| /u `<security_package_id>` | セキュリティ パッケージ (セキュリティ プロバイダー) を指定の呼び出しに RPC を使用します。 セキュリティ パッケージは、数値または名として識別されます。 数値を使用する場合、RpcBindingSetAuthInfoEx API と同様に同じ数とは。 このオプションを指定する場合は、 *[なし*] 以外の認証レベルを指定する必要があります。 このオプションには既定値はありません。 指定されていない場合、RPC は ping にセキュリティを使用しません。 次の一覧は、名前と番号を表示します。 名前は大文字小文字が区別されません。<ul><li>Negotiate/9 またはネゴシエーション、snego、negotiate のいずれか</li><li>NTLM/10 または NTLM</li><li>SChannel/14 または SChannel</li><li>Kerberos/16 または Kerberos</li><li>カーネル/20 またはカーネル</li></ul> |
| /a `<authn_level>` | 使用する認証レベルを指定します。 このオプションを指定する場合は、セキュリティパッケージ ID (**/u**) も指定する必要があります。 このオプションが指定されていない場合、RPC では ping にセキュリティが使用されません。 このオプションには既定値はありません。 設定可能な値は、次のとおりです。<ul><li>接続する</li><li>call</li><li>pkt</li><li>整合性 (integrity)</li><li>privacy</li></ul> |
| Ms-dos `<server_princ_name>` | サーバー プリンシパル名を指定します。<p>このフィールドはのみに使用できる認証レベルとセキュリティ パッケージが選択されている場合。 |
| /I `<auth_identity>` | サーバーに接続する別の id を指定できます。 Id は、フォームのユーザー、ドメイン、パスワードは。 ユーザー名、ドメイン、またはパスワードには、シェルによって解釈できる特殊文字がある場合は、id を二重引用符で囲みます。 指定できます `\*` パスワードと RPC ではなくするように求められます画面にエコーせず、パスワードを入力します。 このフィールドが指定されていない場合、ログオン ユーザーの id が使用されます。<p>このフィールドはのみに使用できる認証レベルとセキュリティ パッケージが選択されている場合。 |
| スイッチ `<capabilities>` | フラグの 16 進数のビットマスクを指定します。 このフィールドはのみに使用できる認証レベルとセキュリティ パッケージが選択されている場合。 |
| /T `<identity_tracking>` | 静的または動的を指定します。 表示しない場合は、既定値を指定すると、動的ができます。<p>このフィールドはのみに使用できる認証レベルとセキュリティ パッケージが選択されている場合。 |
| /M `<impersonation_type>` | 匿名である、指定識別、権限を借用または委任します。 既定値は、権限を借用します。<p>このフィールドはのみに使用できる認証レベルとセキュリティ パッケージが選択されている場合。 |
| /S `<server_sid>` | サーバーの予期される SID を指定します。<p>このフィールドはのみに使用できる認証レベルとセキュリティ パッケージが選択されている場合。 |
| /P `<proxy_auth_identity>` | RPC/HTTP プロキシに認証する id を指定します。 **/I**オプションと同じ形式です。 このオプションを使用するには、セキュリティパッケージ (**/u**)、認証レベル (**/a**)、および認証方式 (**/h**) を指定する必要があります。 |
| /F `<RPCHTTP_flags>` | RPC/HTTP フロント エンドの認証に渡すフラグを指定します。 フラグは、数値または現在認識されているフラグは、名前として指定できます。<ul><li>SSL/1 または ssl または use_ssl を使用する</li><li>最初の認証スキーム/2、または最初または use_first を使用する</li></ul>このオプションを使用するには、セキュリティパッケージ (**/u**) および認証レベル (**/a**) を指定する必要があります。 |
| /H `<RPC/HTTP_authn_schemes>` | RPC/HTTP フロント エンドの認証に使用する認証スキームを指定します。 このオプションは、数値またはコンマで区切られた名前の一覧を示します。 例: Basic の場合は、NTLM できます。 認識できる値は (名前は大文字小文字を区別)。<ul><li>Basic/1 または Basic</li><li>NTLM/2 または NTLM</li><li>Certificate/65536 または Cert</li></ul><p>このオプションを使用するには、セキュリティパッケージ (**/u**) および認証レベル (**/a**) を指定する必要があります。 |
| /B `<server_certificate_subject>` | サーバー証明書のサブジェクトを指定します。 このオプションの SSL を使用して、操作する必要があります。<p>このオプションを使用するには、セキュリティパッケージ (**/u**) および認証レベル (**/a**) を指定する必要があります。 |
| /b | サーバーによって送信された証明書からサーバー証明書のサブジェクトを取得し、画面またはログ ファイルに出力します。 Proxy echo only オプション (/E) と [SSL を使用する] オプションが指定されている場合にのみ有効です。<p>このオプションを使用するには、セキュリティパッケージ (**/u**) および認証レベル (**/a**) を指定する必要があります。 |
| /R | HTTP プロキシを指定します。 場合 *なし*, 、RPC プロキシを使用します。 値 *既定* IE 設定、クライアント コンピューターで使用することを意味します。 その他の値は、明示的な HTTP プロキシとして扱われます。 このフラグを指定しないと、既定値が使用、つまり、IE の設定がチェックされます。 このフラグは、 **/e** (echo only) フラグが有効になっている場合にのみ有効です。 |
| /E | Ping を RPC/HTTP プロキシのみに制限します。 Ping がサーバーに到達しません。 RPC/HTTP プロキシが到達可能かどうかを確立しようとしている場合に役立ちます。 HTTP プロキシを指定するには、/R フラグを使用します。 HTTP プロキシが/o フラグで指定されている場合は、このオプションは無視されます。<p>このオプションを使用するには、セキュリティパッケージ (**/u**) および認証レベル (**/a**) を指定する必要があります。 |
| /q | クワイエット モードを指定します。 パスワードを除いて、画面の指示を発行しません。 前提としています *Y* すべてクエリに応答します。 慎重にこのオプションを使用してください。 |
| /c | スマート カード証明書を使用します。 rpcping は、ユーザーにスマートカードの選択を求めるメッセージを表示します。 |
| /A | HTTP プロキシへの認証に使用する id を指定します。 /I オプションの場合と同じ形式があります。<p>このオプションを使用するには、認証スキーム (/U)、セキュリティパッケージ (**/u**)、および認証レベル (**/a**) を指定する必要があります。 |
| /U | HTTP プロキシ認証に使用する認証スキームを指定します。 このオプションは、数値またはコンマで区切られた名前の一覧を示します。 例: Basic の場合は、NTLM できます。 認識できる値は (名前は大文字小文字を区別)。<ul><li>Basic/1 または Basic</li><li>NTLM/2 または NTLM</li></ul>このオプションを使用するには、セキュリティパッケージ (**/u**) および認証レベル (**/a**) を指定する必要があります。 |
| /r | 何度も繰り返しを指定すると、ある場合は、このオプションは、 **rpcping** 現在の実行統計情報の表示定期的に代わりに最後に呼び出した後。 レポートの間隔は秒単位で指定します。 既定値は 15 です。 |
| /v | 指示 **rpcping** 出力に詳細な方法です。 既定値は 1 です。 2 および 3 を指定すると、複数の出力から **rpcping**します。 |
| /d | RPC の発表ネットワーク診断の UI があります。 |
| /p | 認証が失敗した場合に、資格情報が要求を指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

RPC/HTTP 経由で接続する Exchange サーバーにアクセスできるかどうかを確認するには、次のように入力します。

```
rpcping /t ncacn_http /s exchange_server /o RpcProxy=front_end_proxy /P username,domain,* /H Basic /u NTLM /a connect /F 3
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
