---
title: wecutil
description: 「Wecutil コマンドの参照記事。リモートコンピューターから転送されるイベントのサブスクリプションを作成および管理できます。
ms.topic: reference
ms.assetid: 0c82a6cb-d652-429c-9c3d-0f568c78d54b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.openlocfilehash: 52ce6018a0aaf6ff10d6e231092464451d80e1b9
ms.sourcegitcommit: 28b5ab74cb0b40539ccc1a83998d6391e87fe51f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96614914"
---
# <a name="wecutil"></a>wecutil

リモートコンピューターから転送されるイベントのサブスクリプションを作成および管理できます。 リモートコンピューターは、WS-Management プロトコルをサポートしている必要があります。

> [!IMPORTANT]
> "RPC サーバーは使用できませんか?" というメッセージが表示された場合は、「wecutil を実行しようとすると、Windows イベントコレクターサービス (wecsvc) を開始する必要があります。 Wecsvc を起動するには、管理者特権のコマンドプロンプトで「」と入力 `net start wecsvc` します。

## <a name="syntax"></a>構文

```command
wecutil [{es | enum-subscription}] [{gs | get-subscription} <Subid> [/f:<Format>] [/uni:<Unicode>]] [{gr | get-subscriptionruntimestatus} <Subid> [<Eventsource> …]] [{ss | set-subscription} [<Subid> [/e:[<Subenabled>]] [/esa:<Address>] [/ese:[<Srcenabled>]] [/aes] [/res] [/un:<Username>] [/up:<Password>] [/d:<Desc>] [/uri:<Uri>] [/cm:<Configmode>] [/ex:<Expires>] [/q:<Query>] [/dia:<Dialect>] [/tn:<Transportname>] [/tp:<Transportport>] [/dm:<Deliverymode>] [/dmi:<Deliverymax>] [/dmlt:<Deliverytime>] [/hi:<Heartbeat>] [/cf:<Content>] [/l:<Locale>] [/ree:[<Readexist>]] [/lf:<Logfile>] [/pn:<Publishername>] [/essp:<Enableport>] [/hn:<Hostname>] [/ct:<Type>]] [/c:<Configfile> [/cun:<Username> /cup:<Password>]]] [{cs | create-subscription} <Configfile> [/cun:<Username> /cup:<Password>]] [{ds | delete-subscription} <Subid>] [{rs | retry-subscription} <Subid> [<Eventsource>…]] [{qc | quick-config} [/q:[<quiet>]]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `{es | enum-subscription}` | 存在するすべてのリモートイベントサブスクリプションの名前が表示されます。 |
| `{gs | get-subscription} <Subid> [/f:<Format>] [/uni:<Unicode>]` | リモートサブスクリプションの構成情報を表示します。 `<Subid>` サブスクリプションを一意に識別する文字列です。 これは、 `<SubscriptionId>` サブスクリプションの作成に使用された XML 構成ファイルのタグで指定した文字列と同じです。 |
| `{gr | get-subscriptionruntimestatus} <Subid> [<Eventsource> …]` | サブスクリプションのランタイムの状態を表示します。 `<Subid>` サブスクリプションを一意に識別する文字列です。 これは、 `<SubscriptionId>` サブスクリプションの作成に使用された XML 構成ファイルのタグで指定した文字列と同じです。 `<Eventsource>` は、イベントのソースとして機能するコンピューターを識別する文字列です。 完全修飾ドメイン名、NetBIOS 名、または IP アドレスを指定する必要があります。 |
| `{ss | set-subscription} <Subid> [/e:[<Subenabled>]] [/esa:<Address>] [/ese:[<Srcenabled>]] [/aes] [/res] [/un:<Username>] [/up:<Password>] [/d:<Desc>] [/uri:<Uri>] [/cm:<Configmode>] [/ex:<Expires>] [/q:<Query>] [/dia:<Dialect>] [/tn:<Transportname>] [/tp:<Transportport>] [/dm:<Deliverymode>] [/dmi:<Deliverymax>] [/dmlt:<Deliverytime>] [/hi:<Heartbeat>] [/cf:<Content>] [/l:<Locale>] [/ree:[<Readexist>]] [/lf:<Logfile>] [/pn:<Publishername>] [/essp:<Enableport>] [/hn:<Hostname>] [/ct:<Type>]` <br>**OR**<br>`{ss | set-subscription /c:<Configfile> [/cun:<Comusername> /cup:<Compassword>]` | サブスクリプションの構成を変更します。 サブスクリプション ID と、サブスクリプションパラメーターを変更するための適切なオプションを指定できます。また、XML 構成ファイルを指定してサブスクリプションパラメーターを変更することもできます。 |
| `{cs | create-subscription} <Configfile> [/cun:<Username> /cup:<Password>]` | リモートサブスクリプションを作成します。 `<Configfile>` サブスクリプション構成を含む XML ファイルへのパスを指定します。 絶対パスまたは現在のディレクトリを基準とした相対パスを指定できます。 |
| `{ds | delete-subscription} <Subid>` | サブスクリプションのイベントログにイベントを配信するすべてのイベントソースからサブスクリプションとアンサブスクライブを削除します。 既に受信してログに記録されているイベントは削除されません。 `<Subid>` サブスクリプションを一意に識別する文字列です。 これは、 `<SubscriptionId>` サブスクリプションの作成に使用された XML 構成ファイルのタグで指定した文字列と同じです。 |
| `{rs | retry-subscription} <Subid> [<Eventsource>…]` | 接続の確立を再試行し、アクティブでないサブスクリプションにリモートサブスクリプション要求を送信します。 すべてのイベントソースまたは指定されたイベントソースの再アクティブ化を試みます。 無効なソースは再試行されません。 `<Subid>` サブスクリプションを一意に識別する文字列です。 これは、 `<SubscriptionId>` サブスクリプションの作成に使用された XML 構成ファイルのタグで指定した文字列と同じです。 `<Eventsource>` は、イベントのソースとして機能するコンピューターを識別する文字列です。 完全修飾ドメイン名、NetBIOS 名、または IP アドレスを指定する必要があります。 |
| `{qc | quick-config} [/q:[<Quiet>]]` | Windows イベントコレクターサービスを構成して、再起動によってサブスクリプションが作成され、維持されるようにします。 これには、次の手順が含まれます。<ol><li>ForwardedEvents チャネルが無効になっている場合は有効にします。</li><li>Windows イベントコレクターサービスの開始を遅延するように設定します。</li><li>Windows イベントコレクターサービスが実行されていない場合は、開始します。</li></ol> |

#### <a name="options"></a>Options

| オプション | 説明 |
|--|--|
| /f`<Format>` | 表示される情報の形式を指定します。 `<Format>` XML または簡潔にすることができます。 **Xml** の場合、出力は xml 形式で表示されます。 **簡潔** な場合は、名前と値のペアに出力が表示されます。 既定値は **簡潔** です。 |
| スイッチ`<Configfile>` | サブスクリプション構成を含む XML ファイルへのパスを指定します。 絶対パスまたは現在のディレクトリを基準とした相対パスを指定できます。 このオプション **は、その他のオプション** と同時に使用 **/cup** することはできません。 |
| /e: [ `<Subenabled>` ] | サブスクリプションを有効または無効にします。 `<Subenabled>` true または false を指定できます。 このオプションの既定値は **true** です。 |
| esa`<Address>` | イベントソースのアドレスを指定します。 `<Address>` イベントのソースとして機能するコンピューターを識別する、完全修飾ドメイン名、NetBIOS 名、または IP アドレスを含む文字列です。 このオプションは、 **/ese**、 **/aes**、 **/res**、/ **un** 、および/ **up** オプションと共に使用してください。 |
| /ese: [ `<Srcenabled>` ] | イベントソースを有効または無効にします。 `<Srcenabled>` true または false を指定できます。 このオプションは、 **/esa** オプションが指定されている場合にのみ使用できます。 このオプションの既定値は **true** です。 |
| /aes | サブスクリプションにまだ含まれていない場合は、 **/esa** オプションで指定されたイベントソースを追加します。 **/Esa** オプションで指定されたアドレスが既にサブスクリプションの一部である場合は、エラーが報告されます。 このオプションは、 **/esa** オプションが指定されている場合にのみ使用できます。 |
| /res | サブスクリプションに既に含まれている場合は、 **/esa** オプションによって指定されたイベントソースを削除します。 **/Esa** オプションで指定されたアドレスがサブスクリプションの一部ではない場合は、エラーが報告されます。 このオプションは、 **/esa** オプションが指定されている場合にのみ使用できます。 |
| ウン`<Username>` | **/Esa** オプションで指定されたイベントソースで使用するユーザー資格情報を指定します。 このオプションは、 **/esa** オプションが指定されている場合にのみ使用できます。 |
| /up`<Password>` | ユーザー資格情報に対応するパスワードを指定します。 このオプションは、 **/un** オプションが指定されている場合にのみ使用できます。 |
| d`<Desc>` | サブスクリプションの説明を提供します。 |
| uri`<Uri>` | サブスクリプションによって使用されるイベントの種類を指定します。 `<Uri>` イベントのソースを一意に識別するために、イベントソースコンピューターのアドレスと組み合わせた URI 文字列を格納します。 URI 文字列は、サブスクリプション内のすべてのイベントソースアドレスに使用されます。 |
| /cm`<Configmode>` | 構成モードを設定します。 `<Configmode>` には、次の文字列のいずれかを指定できます: **Normal**、 **Custom**、 **Minlatency** 、または **minlatency 幅**。 **通常**、 **Minlatency**、および **minlatency 幅** モードでは、配信モード、配信の最大項目数、ハートビート間隔、配信の最大待機時間を設定します。 構成モードが "**カスタム**" に設定されている場合にのみ、/ **dm**、/ **dmi**、/ **hi** 、/ **dmlt** オプションを指定できます。 |
| エックス`<Expires>` | サブスクリプションの有効期限が切れる時刻を設定します。 `<Expires>` は、標準 XML または元の日付/時刻形式で定義する必要があります。 `yyyy-MM-ddThh:mm:ss[.sss][Z]` ここで、 *T* は時刻の区切り記号で、 *Z* は UTC 時刻を示します。 |
| /q`<Query>` | サブスクリプションのクエリ文字列を指定します。 の形式は、 `<Query>` URI 値が異なる場合があり、サブスクリプション内のすべてのソースに適用されます。 |
| dia`<Dialect>` | クエリ文字列で使用する言語を定義します。 |
| /tn`<Transportname>` | リモートイベントソースへの接続に使用するトランスポートの名前を指定します。 |
| /tp`<Transportport>` | リモートイベントソースへの接続時にトランスポートによって使用されるポート番号を設定します。 |
| data`<Deliverymode>` | 配信モードを指定します。 `<Deliverymode>` プルまたはプッシュのいずれかを指定できます。 このオプションは、 **/cm** オプションが **Custom** に設定されている場合にのみ有効です。 |
| dmi`<Deliverymax>` | バッチ配信の項目の最大数を設定します。 このオプションは、 **/cm** が **Custom** に設定されている場合にのみ有効です。 |
| /dmlt:`<Deliverytime>` | イベントのバッチ配信の最大待機時間を設定します。 `<Deliverytime>` ミリ秒数を指定します。 このオプションは、 **/cm** が Custom に設定されている場合にのみ有効です。 |
| ようこそ`<Heartbeat>` | ハートビートの間隔を定義します。 `<Heartbeat>` ミリ秒数を指定します。 このオプションは、 **/cm** が **Custom** に設定されている場合にのみ有効です。 |
| cf`<Content>` | 返されるイベントの形式を指定します。 `<Content>` イベントまたは RenderedText を指定できます。 値が **Renderedtext** の場合、イベントに添付されたローカライズされた文字列 (イベントの説明など) と共にイベントが返されます。 既定値は **Renderedtext** です。 |
| /l:`<Locale>` | RenderedText 形式でローカライズされた文字列を配信するためのロケールを指定します。 `<Locale>` は言語と国/地域 id で、たとえば EN-US を使用します。 このオプションは、 **/cf** オプションが **renderedtext** に設定されている場合にのみ有効です。 |
| /: [ `<Readexist>` ] | サブスクリプションに対して配信されるイベントを識別します。 `<Readexist>` true または false を使用できます。 `<Readexist>`が true の場合、既存のすべてのイベントがサブスクリプションのイベントソースから読み込まれます。 `<Readexist>`が false の場合、将来の (到着した) イベントのみが配信されます。 既定値は、 **////** オプションの値が指定されていない場合に **true** になります。 **/** のオプションを指定しない場合、既定値は **false** になります。 |
| lf`<Logfile>` | イベントソースから受信したイベントを格納するために使用されるローカルイベントログを指定します。 |
| pn`<Publishername>` | 発行元の名前を指定します。 **/Lf** オプションで指定されたログを所有またはインポートするパブリッシャーである必要があります。 |
| /essp:`<Enableport>` | リモートサービスのサービスプリンシパル名にポート番号を追加する必要があることを指定します。 `<Enableport>` true または false を指定できます。 が true の場合、ポート番号が付加され `<Enableport>` ます。 ポート番号を追加すると、イベントソースへのアクセスが拒否されるのを防ぐために、一部の構成が必要になる場合があります。 |
| hn`<Hostname>` | ローカルコンピューターの DNS 名を指定します。 この名前は、イベントをプッシュするためにリモートイベントソースによって使用されます。プッシュサブスクリプションの場合にのみ使用する必要があります。 |
| /ct`<Type>` | リモートソースアクセスの資格情報の種類を設定します。 `<Type>` の値は、 **default**、 **negotiate**、 **digest**、 **basic** 、または **localmachine** のいずれかにする必要があります。 既定値は **default** です。 |
| /cun:`<Comusername>` | 独自のユーザー資格情報を持たないイベントソースに使用する共有ユーザー資格情報を設定します。 このオプションを **/c** オプションと共に指定した場合、構成ファイルからの個々のイベントソースのユーザー名と UserPassword の設定は無視されます。 特定のイベントソースに対して別の資格情報を使用する場合は、別の **ss** コマンドのコマンドラインで特定のイベントソースに対して **/un** オプションと **/up** オプションを指定することによって、この値を上書きする必要があります。 |
| カップ`<Compassword>` | 共有ユーザー資格情報のユーザーパスワードを設定します。 `<Compassword>`が * (アスタリスク) に設定されている場合、パスワードはコンソールから読み込まれます。 このオプションは、 **/cun** オプションが指定されている場合にのみ有効です。 |
| /q: [ `<Quiet>` ] | 構成手順で確認を求めるメッセージを表示するかどうかを指定します。 `<Quiet>` true または false を指定できます。 `<Quiet>`が true の場合、構成手順によって確認メッセージが表示されません。 このオプションの既定値は **false** です。 |

## <a name="examples"></a>例

構成ファイルの内容を表示するには、次のように入力します。

```XML
<Subscription xmlns=https://schemas.microsoft.com/2006/03/windows/events/subscription>
<Uri>https://schemas.microsoft.com/wbem/wsman/1/windows/EventLog</Uri>
<!-- Use Normal (default), Custom, MinLatency, MinBandwidth -->
<ConfigurationMode>Normal</ConfigurationMode>
  <Description>Forward Sample Subscription</Description>
  <SubscriptionId>SampleSubscription</SubscriptionId>
  <Query><![CDATA[
    <QueryList>
      <Query Path=Application>
        <Select>*</Select>
      </Query>
    </QueryList>]]
  </Query>
<EventSources>
  <EventSource Enabled=true>
    <Address>mySource.myDomain.com</Address>
    <UserName>myUserName</UserName>
    <Password>*</Password>
  </EventSource>
</EventSources>
<CredentialsType>Default</CredentialsType>
<Locale Language=EN-US></Locale>
</Subscription>
```

*Sub1* という名前のサブスクリプションの出力構成情報を表示するには、次のように入力します。

```command
wecutil gs sub1
```

出力例:

```output
EventSource[0]:
Address: localhost
Enabled: true
Description: Subscription 1
Uri: wsman:microsoft/logrecord/sel
DeliveryMode: pull
DeliveryMaxSize: 16000
DeliveryMaxItems: 15
DeliveryMaxLatencyTime: 1000
HeartbeatInterval: 10000
Locale:
ContentFormat: renderedtext
LogFile: HardwareEvents
```

Sub1 という名前のサブスクリプションのランタイム状態を表示するには、次のように入力します。

```command
wecutil gr sub1
```

*WsSelRg2.xml* という名前の新しい XML ファイルから、 *sub1* という名前のサブスクリプション構成を更新するには、次のように入力します。

```command
wecutil ss sub1 /c:%Windir%system32WsSelRg2.xml
```

複数のパラメーターを使用して *sub2* という名前のサブスクリプション構成を更新するには、次のように入力します。

```command
wecutil ss sub2 /esa:myComputer /ese /un:uname /up:* /cm:Normal
```

*Sub1* という名前のサブスクリプションを削除するには、次のように入力します。
```
wecutil ds sub1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
