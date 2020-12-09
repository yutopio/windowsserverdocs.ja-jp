---
title: DNS クエリへのフィルターの適用に DNS ポリシーを使用する
description: このトピックは、Windows Server 2016 の DNS ポリシーシナリオガイドに含まれています。
manager: brianlic
ms.topic: article
ms.assetid: b86beeac-b0bb-4373-b462-ad6fa6cbedfa
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 4f309a304e4457b27eec0ae41d581c5a7bf9bd50
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96865341"
---
# <a name="use-dns-policy-for-applying-filters-on-dns-queries"></a>DNS クエリへのフィルターの適用に DNS ポリシーを使用する

>適用先:Windows Server (半期チャネル)、Windows Server 2016

このトピックでは、 &reg; 指定した条件に基づいたクエリフィルターを作成するために、Windows Server 2016 で DNS ポリシーを構成する方法について説明します。

Dns ポリシーのクエリフィルターを使用すると、dns クエリを送信する dns クエリと dns クライアントに基づいて、カスタムの方法で応答するように DNS サーバーを構成できます。

たとえば、既知の悪意のあるドメインからの dns クエリをブロックするクエリフィルターブロックリストを使用して DNS ポリシーを構成できます。これにより、DNS がこれらのドメインからのクエリに応答しなくなります。 DNS サーバーから応答が送信されないため、悪意のあるドメインメンバーの DNS クエリはタイムアウトします。

別の例として、特定のクライアントセットだけが特定の名前を解決できるようにするクエリフィルター許可リストを作成します。

## <a name="query-filter-criteria"></a><a name="bkmk_criteria"></a> クエリのフィルター条件
次の条件の論理的な組み合わせ (またはその両方) を使用して、クエリフィルターを作成できます。

|名前|説明|
|-----------------|---------------------|
|クライアントサブネット|定義済みのクライアントのサブネットの名前です。 クエリの送信元となるサブネットを確認するために使用します。|
|トランスポート プロトコル|トランスポート プロトコル クエリで使用をします。 指定できる値は、UDP と TCP です。|
|インターネット プロトコル|クエリで使用されるネットワーク プロトコルです。 指定できる値は、IPv4 と IPv6 です。|
|サーバーインターフェイスの IP アドレス|DNS 要求を受信した DNS サーバーのネットワークインターフェイスの IP アドレス。|
|FQDN|ワイルドカードを使用する可能性がある、クエリ内のレコードの完全修飾ドメイン名。|
|クエリの型|クエリ対象のレコードの種類、 \( SRV、TXT など \) 。|
|時刻|クエリが受信した時刻。|

次の例は、dns 名前解決のクエリをブロックまたは許可する DNS ポリシーのフィルターを作成する方法を示しています。

>[!NOTE]
>このトピックのコマンド例では、Windows PowerShell コマンド **DnsServerQueryResolutionPolicy** を使用します。 詳細については、次を参照してください。 [追加 DnsServerQueryResolutionPolicy](/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy)します。

## <a name="block-queries-from-a-domain"></a><a name="bkmk_block1"></a>ドメインからのクエリをブロックする

場合によっては、悪意のあるドメインの DNS 名解決、または組織の使用ガイドラインに準拠していないドメインの DNS 名前解決をブロックする必要があります。 DNS ポリシーを使用して、ドメインのブロックしているクエリを実行できます。

この例で構成したポリシーは、特定のゾーンでは作成されません。代わりに、DNS サーバーで構成されているすべてのゾーンに適用されるサーバーレベルのポリシーを作成します。 サーバーレベルのポリシーは最初に評価されるため、DNS サーバーがクエリを受信したときに最初に照合されます。

次のコマンド例では、ドメイン **サフィックス contosomalicious.com** を使用してクエリをブロックするようにサーバーレベルポリシーを構成します。

`
Add-DnsServerQueryResolutionPolicy -Name "BlockListPolicy" -Action IGNORE -FQDN "EQ,*.contosomalicious.com" -PassThru
`

>[!NOTE]
>**Action** パラメーターの値を **IGNORE** に設定すると、DNS サーバーは応答なしのクエリを削除するように構成されます。 これにより、悪意のあるドメインの DNS クライアントがタイムアウトします。

## <a name="block-queries-from-a-subnet"></a><a name="bkmk_block2"></a>サブネットからのクエリをブロックする
この例では、一部のマルウェアに感染していて、DNS サーバーを使用して悪意のあるサイトに接続しようとしていることが検出された場合、サブネットからのクエリをブロックできます。

' Add-DnsServerClientSubnet-Name "MaliciousSubnet06"-IPv4Subnet 172.0.33.0/24-PassThru

Add-DnsServerQueryResolutionPolicy-Name "BlockListPolicyMalicious06"-Action IGNORE-ClientSubnet "EQ, MaliciousSubnet06"-PassThru "

次の例では、サブネット条件を FQDN 条件と組み合わせて使用して、感染したサブネットから特定の悪意のあるドメインのクエリをブロックする方法を示します。

`
Add-DnsServerQueryResolutionPolicy -Name "BlockListPolicyMalicious06" -Action IGNORE -ClientSubnet  "EQ,MaliciousSubnet06" –FQDN “EQ,*.contosomalicious.com” -PassThru
`

## <a name="block-a-type-of-query"></a><a name="bkmk_block3"></a>クエリの種類をブロックする
場合によっては、サーバー上の特定の種類のクエリの名前解決をブロックする必要があります。 たとえば、"ANY" クエリをブロックして、不正に使用して増幅攻撃を作成することができます。

`
Add-DnsServerQueryResolutionPolicy -Name "BlockListPolicyQType" -Action IGNORE -QType "EQ,ANY" -PassThru
`

## <a name="allow-queries-only-from-a-domain"></a><a name="bkmk_allow1"></a>ドメインからのクエリのみを許可する
DNS ポリシーを使用してクエリをブロックすることはできません。クエリを使用して、特定のドメインまたはサブネットからのクエリを自動的に承認することができます。 許可リストを構成すると、DNS サーバーは、許可されているドメインからのクエリのみを処理し、他のドメインからの他のすべてのクエリをブロックします。

次のコマンド例では、contoso.com ドメインと子ドメイン内のコンピューターとデバイスのみが DNS サーバーを照会できます。

`
Add-DnsServerQueryResolutionPolicy -Name "AllowListPolicyDomain" -Action IGNORE -FQDN "NE,*.contoso.com" -PassThru
`

## <a name="allow-queries-only-from-a-subnet"></a><a name="bkmk_allow2"></a>サブネットからのクエリのみを許可する
また、IP サブネットの許可リストを作成して、これらのサブネットから送信されていないすべてのクエリが無視されるようにすることもできます。

`
Add-DnsServerClientSubnet -Name "AllowedSubnet06" -IPv4Subnet 172.0.33.0/24 -PassThru
`
`
Add-DnsServerQueryResolutionPolicy -Name "AllowListPolicySubnet” -Action IGNORE -ClientSubnet  "NE, AllowedSubnet06" -PassThru
`

## <a name="allow-only-certain-qtypes"></a><a name="bkmk_allow3"></a>特定の QTypes のみを許可する
QTYPEs には許可リストを適用できます。

たとえば、外部の顧客が DNS サーバーインターフェイス164.8.1.1 に対してクエリを実行している場合は、特定の QTYPEs のみに対してクエリを実行できます。一方、内部サーバーが名前解決または監視のために使用する SRV レコードや TXT レコードなどの他の QTYPEs もあります。

`
Add-DnsServerQueryResolutionPolicy -Name "AllowListQType" -Action IGNORE -QType "NE,A,AAAA,MX,NS,SOA" –ServerInterface “EQ,164.8.1.1” -PassThru
`

何千もの DNS のポリシーに合わせて作成できます、トラフィック管理の要件、DNS サーバーを再起動しなくても - 受信したクエリで、すべての新しいポリシーが動的 - 適用されます。
