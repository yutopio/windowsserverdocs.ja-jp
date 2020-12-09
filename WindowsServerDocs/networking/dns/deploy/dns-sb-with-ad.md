---
title: Active Directory でスプリット ブレイン DNS に DNS ポリシーを使用する
description: このトピックを使用して、Windows Server 2016 で Active Directory 統合 DNS ゾーンを使用して、スプリットブレイン展開の DNS ポリシーのトラフィック管理機能を活用できます。
manager: brianlic
ms.topic: article
ms.assetid: f9533204-ad7e-4e49-81c1-559324a16aeb
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 423debd6538e2de8de7e2919e18e7da39fe8c733
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96865331"
---
# <a name="use-dns-policy-for-split-brain-dns-in-active-directory"></a>Active Directory でスプリット ブレイン DNS に DNS ポリシーを使用する

>適用先:Windows Server (半期チャネル)、Windows Server 2016

このトピックを使用すると、 \- Windows Server 2016 で Active Directory 統合 dns ゾーンを使用して、スプリットブレイン展開の dns ポリシーのトラフィック管理機能を活用できます。

Windows Server 2016 では、DNS ポリシーのサポートは、統合された DNS ゾーンを Active Directory するように拡張されています。 Active Directory 統合によっ \- て、DNS サーバーに複数のマスターの高可用性機能が提供されます。

以前は、このシナリオは、DNS 管理者の管理 2 台の DNS サーバー、各内部および外部のユーザーのセットごとにサービスを提供することが必要です。 ゾーン内の少数のレコードだけが分割されている場合、 \- またはゾーンの両方のインスタンス (内部および外部) が同じ親ドメインに委任されていた場合は、管理難問になります。

> [!NOTE]
> - DNS 展開は \- 、1つのゾーンに2つのバージョンがあり、組織のイントラネット上の内部ユーザーに1つのバージョンと、外部ユーザー (通常はインターネット上のユーザー) の1つのバージョンがある場合に分割されます。
> - トピック「 [Split-Brain dns の展開に Dns ポリシーを使用](split-brain-DNS-deployment.md) する」では、dns ポリシーとゾーンのスコープを使用して、 \- 単一の WINDOWS server 2016 dns サーバーに分割ブレイン dns システムを展開する方法について説明します。

## <a name="example-split-brain-dns-in-active-directory"></a>\-Active Directory での分割ブレイン DNS の例

この例では、1 つ架空の企業、www.career.contoso.com で仕事紹介 Web サイトを保持する contoso 社で使用します。

サイトには、内部の求人が利用可能な内部ユーザー用、2 つのバージョンがあります。 この内部サイトは、ローカル IP アドレス 10.0.0.39 から入手できます。

2 番目のバージョンは、パブリック IP アドレス 65.55.39.10 で利用可能な同じサイトのパブリック バージョンです。

DNS のポリシーがない場合を別の Windows Server DNS サーバーでこれら 2 つのゾーンをホストし、それらを個別に管理、管理者が必要です。

DNS ポリシーを使用してこれらのゾーンできますでホストされるよう、同じ DNS サーバーです。

Contoso.com の DNS サーバーが Active Directory 統合されており、2つのネットワークインターフェイスでリッスンしている場合、Contoso の DNS 管理者は、このトピックの手順に従って、スプリットブレインの展開を行うことができ \- ます。

Dns 管理者は、次の IP アドレスを使用して DNS サーバーインターフェイスを構成します。

- インターネットに接続するネットワークアダプターは、外部クエリ用に208.84.0.53 のパブリック IP アドレスで構成されます。
- イントラネットに接続するネットワークアダプターは、内部クエリ用に10.0.0.56 のプライベート IP アドレスを使用して構成されます。

次の図は、このシナリオを示しています。

![AD 統合 DNS 展開の Split-Brain](../../media/DNS-SB-AD/DNS-SB-AD.jpg)

## <a name="how-dns-policy-for-split-brain-dns-in-active-directory-works"></a>Active Directory の Split ブレイン DNS の DNS ポリシーの \- しくみ

必要な DNS ポリシーで、DNS サーバーを構成すると、各名前解決の要求は、DNS サーバー上のポリシーに対して評価されます。

サーバーのインターフェイスは、内部および外部のクライアントを区別するために、この例では、条件として使用されます。

クエリを受信するサーバーのインターフェイスには、任意のポリシーが一致すると、クエリに応答する、関連付けられているゾーンのスコープが使用されます。

そのため、この例ではプライベート ip アドレス (10.0.0.56) で受信した www.career.contoso.com に関する DNS クエリ DNS 応答を受信する内部の IP アドレスを含むパブリック ネットワーク インターフェイスで受信 DNS クエリ応答を受信する DNS ゾーンの既定のスコープ (これは通常のクエリの解決策と同じ) のパブリック IP アドレスを含みます。

動的 DNS DDNS の \( \) 更新と清掃のサポートは、既定のゾーンのスコープでのみサポートされています。 内部クライアントは既定のゾーンのスコープによって処理されるため、Contoso の DNS 管理者は、引き続き既存のメカニズム (動的 DNS または静的) を使用して contoso.com のレコードを更新できます。 \-この例では、外部スコープなどの既定以外のゾーンスコープについ \( ては \) 、DDNS または清掃のサポートは使用できません。

### <a name="high-availability-of-policies"></a>ポリシーの高可用性

DNS ポリシーは Active Directory 統合されていません。 このため、DNS ポリシーは、同じ Active Directory 統合ゾーンをホストしている他の DNS サーバーにはレプリケートされません。

DNS ポリシーは、ローカル DNS サーバーに格納されます。 次の Windows PowerShell コマンドの例を使用すると、DNS ポリシーをサーバー間で簡単にエクスポートできます。

```powershell
$policies = Get-DnsServerQueryResolutionPolicy -ZoneName "contoso.com" -ComputerName Server01
$policies |  Add-DnsServerQueryResolutionPolicy -ZoneName "contoso.com" -ComputerName Server02
```

詳細については、次の Windows PowerShell のリファレンストピックを参照してください。

- [DnsServerQueryResolutionPolicy](/powershell/module/dnsserver/get-dnsserverqueryresolutionpolicy)
- [DnsServerQueryResolutionPolicy](/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy)

## <a name="how-to-configure-dns-policy-for-split-brain-dns-in-active-directory"></a>\-Active Directory で Split ブレイン dns の Dns ポリシーを構成する方法

Dns ポリシーを使用して DNS Split-Brain の展開を構成するには、次のセクションを使用する必要があります。詳細な構成手順については、「」を参照してください。

### <a name="add-the-active-directory-integrated-zone"></a>Active Directory 統合ゾーンを追加する

次のコマンド例を使用して、Active Directory 統合 contoso.com ゾーンを DNS サーバーに追加できます。

```powershell
Add-DnsServerPrimaryZone -Name "contoso.com" -ReplicationScope "Domain" -PassThru
```

詳細については、「 [デモンストレーション](/powershell/module/dnsserver/add-dnsserverprimaryzone)」を参照してください。

### <a name="create-the-scopes-of-the-zone"></a>ゾーンのスコープを作成します。

このセクションを使用すると、ゾーン contoso.com をパーティション分割して外部ゾーンスコープを作成できます。

ゾーンのスコープは、ゾーンの一意のインスタンスです。 DNS ゾーンは複数のゾーンスコープを持つことができ、各ゾーンスコープには独自の DNS レコードセットが含まれます。 同じレコードが複数のスコープに存在し、異なる IP アドレスまたは同じ IP アドレスを持つことができます。

この新しいゾーンスコープを Active Directory 統合ゾーンに追加するので、ゾーンのスコープとその中のレコードは、Active Directory 経由でドメイン内の他のレプリカサーバーにレプリケートされます。

既定では、ゾーンスコープはすべての DNS ゾーンに存在します。 このゾーンのスコープでは、ゾーンと同じ名前と、従来の DNS の機能がこのスコープで動作します。 この既定のゾーンスコープは、www.career.contoso.com の内部バージョンをホストします。

次のコマンド例を使用すると、DNS サーバーでゾーンのスコープを作成できます。

```powershell
Add-DnsServerZoneScope -ZoneName "contoso.com" -Name "external"
```

詳細については、「 [DnsServerZoneScope](/powershell/module/dnsserver/add-dnsserverzonescope)」を参照してください。

### <a name="add-records-to-the-zone-scopes"></a>レコードをゾーンのスコープに追加します。

次の手順では、web サーバーホストを表すレコードを、外部と内部クライアントの既定の2つのゾーンスコープに追加し \( \) ます。

既定の内部ゾーンスコープでは、レコード www.career.contoso.com は、プライベート IP アドレスである IP アドレス10.0.0.39 を使用して追加されます。外部ゾーンスコープでは、同じレコード \( www.career.contoso.com \) がパブリック IP アドレス65.55.39.10 と共に追加されます。

既定の \( 内部ゾーンスコープと外部ゾーンスコープの両方のレコードは、 \)  それぞれのゾーンスコープと共にドメイン全体に自動的にレプリケートされます。

次のコマンド例を使用すると、DNS サーバーのゾーンスコープにレコードを追加できます。

```powershell
Add-DnsServerResourceRecord -ZoneName "contoso.com" -A -Name "www.career" -IPv4Address "65.55.39.10" -ZoneScope "external"
Add-DnsServerResourceRecord -ZoneName "contoso.com" -A -Name "www.career" -IPv4Address "10.0.0.39”
```

> [!NOTE]
> レコードが既定のゾーンのスコープに追加される場合、 **–ゾーン範囲ゾーン** パラメーターは含まれません。 この操作は、通常のゾーンにレコードを追加することと同じです。

詳細については、次を参照してください。 [追加 DnsServerResourceRecord](/powershell/module/dnsserver/add-dnsserverresourcerecord)します。

### <a name="create-the-dns-policies"></a>DNS のポリシーを作成します。

外部ネットワークおよび内部ネットワーク用のサーバー インターフェイスを識別する、ゾーンのスコープを作成した後は、内部および外部のゾーンのスコープを接続する DNS ポリシーを作成する必要があります。

> [!NOTE]
> この例では、 \( \) 内部および外部のクライアントを区別するための条件として、次の例のコマンドで-serverinterface パラメーターを使用して、サーバーインターフェイスを使用しています。 内部および外部のクライアントを区別するために別の方法では、クライアントのサブネットを使用して、条件として、です。 内部のクライアントが属するサブネットを特定する場合は、クライアントのサブネットに基づいて区別するために DNS のポリシーを構成できます。 クライアントのサブネットの条件を使用したトラフィック管理を構成する方法については、次を参照してください。 [のプライマリ サーバーの地理的な場所ベースのトラフィック管理用の DNS ポリシーを使用して](primary-geo-location.md)します。

ポリシーを構成した後、パブリックインターフェイスで DNS クエリを受信すると、ゾーンの外部スコープから回答が返されます。

> [!NOTE]
> 既定の内部ゾーンスコープをマップするためにポリシーは必要ありません。

```powershell
Add-DnsServerQueryResolutionPolicy -Name "SplitBrainZonePolicy" -Action ALLOW -ServerInterface "eq,208.84.0.53" -ZoneScope "external,1" -ZoneName contoso.com
```

> [!NOTE]
> 208.84.0.53 は、パブリックネットワークインターフェイスの IP アドレスです。

詳細については、次を参照してください。 [追加 DnsServerQueryResolutionPolicy](/powershell/module/dnsserver/add-dnsserverqueryresolutionpolicy)します。

これで、Active Directory 統合された DNS ゾーンを持つスプリットブレインネームサーバーに必要な DNS ポリシーを使用して、DNS サーバーが構成されました。

何千もの DNS のポリシーに合わせて作成できます、トラフィック管理の要件、DNS サーバーを再起動しなくても - 受信したクエリで、すべての新しいポリシーが動的 - 適用されます。
