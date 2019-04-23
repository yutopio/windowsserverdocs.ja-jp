---
ms.assetid: c28c60ff-693d-49ee-a75b-58f24866217b
title: フェデレーション サーバー プロキシの名前解決の要件
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: a94e4de181cd8794d479bbd6695a94658aba0f86
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59855023"
---
# <a name="name-resolution-requirements-for-federation-server-proxies"></a>フェデレーション サーバー プロキシの名前解決の要件

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

インターネット上のクライアント コンピューターが Active Directory フェデレーション サービスで保護されているアプリケーションにアクセスしようとした場合に\(AD FS\)、最初のフェデレーション サーバーを認証する必要があります。 ほとんどの場合、フェデレーション サーバーは通常ありません、インターネットから直接アクセスです。 そのため、インターネット クライアント コンピューターがリダイレクトされるよう、フェデレーション サーバー プロキシを代わりにします。 正常なリダイレクトを実行するには、適切なドメイン ネーム システムを追加する \(DNS\) またはインターネットが直面する複数の DNS ゾーンのレコードです。  
  
フェデレーション サーバー プロキシをインターネット クライアントをリダイレクトするために使用する方法は、境界ネットワーク内の DNS ゾーンを構成する方法や、インターネット上のユーザーが管理する DNS ゾーンの構成方法によって異なります。 フェデレーション サーバー プロキシは、境界ネットワークで使用することが意図されています。 これらのインターネット クライアント要求をリダイレクト フェデレーション サーバーが正常に DNS は、すべてのインターネット上で正しく構成されている場合にのみ\-を制御するゾーンが直面しています。 インターネットに構成することはそのため、\-ゾーンが直面している —、境界ネットワークのみを提供している DNS ゾーンまたは境界ネットワークとインターネット クライアントの両方を提供している DNS ゾーンがあるかどうか-が重要です。  
  
このトピックでは、境界ネットワークにフェデレーション サーバー プロキシを配置すると、名前解決を構成するために行える手順を説明します。 使用する手順を決定するには、最初に、組織の境界ネットワーク内の DNS インフラストラクチャが、次の DNS シナリオのどれに最も近いかを判断します。 その後、そのシナリオの手順を実行します。  
  
## <a name="dns-zone-serving-only-the-perimeter-network"></a>境界ネットワークのみを対象とする DNS ゾーン  
このシナリオで、ユーザーの組織には境界ネットワーク内に 1 つまたは 2 つの DNS ゾーンがあり、ユーザーの組織はインターネット上のどの DNS ゾーンも制御していません。 フェデレーション サーバー プロキシが境界ネットワークのシナリオのみを提供する DNS ゾーンの正常な名前の解決策は、次の条件によって異なります。  
  
-   フェデレーション サーバー プロキシでは、完全修飾ドメイン名を解決するのには、ホスト ファイルの設定が必要 \(FQDN\) のフェデレーション サーバーまたはフェデレーション サーバー クラスターの IP アドレスにフェデレーション サーバーのエンドポイント URL。  
  
-   フェデレーション サーバーのエンドポイント URL の FQDN は、フェデレーション サーバー プロキシの IP アドレスに解決できるように、アカウント パートナーの境界ネットワークに DNS を構成する必要があります。  
  
次の図および対応する手順では、示されている例でこれらの各条件を実現する方法について説明します。 次の図に、Microsoft Network Load Balancing \(NLB\) テクノロジには、1 つ、クラスターの FQDN および既存のフェデレーション サーバー ファームのクラスター IP アドレスを 1 つが用意されています。  
  
![名の要件](media/adfs2_deploy_single_fs.gif)  
  
クラスターの IP アドレスまたはクラスター FQDN の構成の詳細については、NLB を使用して参照してください [クラスター パラメーターを指定して](https://go.microsoft.com/fwlink/?LinkId=75282)します。  
  
### <a name="1-configure-the-hosts-file-on-the-federation-server-proxy"></a>1. フェデレーション サーバー プロキシで hosts ファイルを構成する  
アカウント パートナーのフェデレーション サーバー プロキシが fs.fabrikam.com を実際のアカウント フェデレーション サーバーの IP アドレスに解決するのには、ローカルの hosts ファイルにエントリを持つアカウント フェデレーション サーバー プロキシに fs.fabrikam.com に対するすべての要求を解決するのには、境界ネットワークに DNS が構成されている、ため \(またはフェデレーション サーバー ファームでのクラスター DNS 名\) 企業ネットワークに接続されています。 自体にではなく、アカウント フェデレーション サーバーにホスト名 fs.fabrikam.com を解決するのには、アカウント フェデレーション サーバー プロキシにできるようになります: 境界の DNS を使用して fs.fabrikam.com を検索しようとした場合に発生すると、: フェデレーション サーバー プロキシは、フェデレーション サーバーと通信できるようにします。  
  
### <a name="2-configure-perimeter-dns"></a>2. 境界 DNS を構成する  
のみ単一 AD FS ホスト名がクライアント コンピューターに転送されるため、インターネットまたはイントラネット上されるかどうか-境界 DNS サーバーを使用する、インターネット上のクライアント コンピューターはアカウント フェデレーション サーバーの FQDN を解決する必要があります \(fs.fabrikam.com\) 境界ネットワーク上のアカウント フェデレーション サーバー プロキシの IP アドレスにします。 境界 DNS にはに 1 つのホストに限定 corp.fabrikam.com DNS ゾーンが含まれているように、しようとすると、fs.fabrikam.com を解決するには、ログオン アカウント フェデレーション サーバー プロキシのクライアントを転送できる、 \(A\) fs のリソース レコード \(fs.fabrikam.com\) と境界ネットワーク上のアカウント フェデレーション サーバー プロキシの IP アドレスです。  
  
フェデレーション サーバー プロキシの hosts ファイルを変更して、境界ネットワークに DNS を構成する方法の詳細については、次を参照してください。 [、境界ネットワークのみを提供する DNS ゾーンにフェデレーション サーバー プロキシの名前解決を構成する](../../ad-fs/deployment/Configure-Name-Resolution-for-a-Federation-Server-Proxy-in-a-DNS-Zone-That-Serves-Only-the-Perimeter-Network.md)です。  
  
## <a name="dns-zone-serving-both-the-perimeter-network-and-internet-clients"></a>境界ネットワークとインターネットの両方のクライアントに対応する DNS ゾーン  
このシナリオでは、ユーザーの組織は、境界ネットワーク内の DNS ゾーンと、インターネット上の 1 つ以上の DNS ゾーンを制御しています。 このシナリオでフェデレーション サーバー プロキシの正常な名前の解決策は、次の条件によって異なります。  
  
-   フェデレーション サーバーのホスト名の FQDN が、境界ネットワーク内のフェデレーション サーバー プロキシの IP アドレスに解決できるように、アカウント パートナーのインターネット ゾーンに DNS を構成する必要があります。  
  
-   フェデレーション サーバーのホスト名の FQDN が企業ネットワーク内のフェデレーション サーバーの IP アドレスに解決できるように、アカウント パートナーの境界ネットワークに DNS を構成する必要があります。  
  
次の図および対応する手順では、示されている例でこれらの各条件を実現する方法について説明します。  
  
![名の要件](media/adfs2_deploy_fsp_3DNS.gif)  
  
### <a name="1-configure-perimeter-dns"></a>1. 境界 DNS を構成する  
このシナリオでは、インターネット上の DNS ゾーンを構成することと見なされますので解決するのには制御する要求が行われる特定のエンドポイント URL の \(、fs.fabrikam.com\) 、境界ネットワーク内のフェデレーション サーバー プロキシの境界の企業ネットワーク内のフェデレーション サーバーにこれらの要求を転送する DNS ゾーンも構成する必要があります。  
  
境界の DNS が 1 つのホストで構成されているので、しようとすると、fs.fabrikam.com を解決するには、アカウント フェデレーション サーバーにクライアントを転送できる、 \(A\) fs のリソース レコード \(fs.fabrikam.com\) と企業ネットワーク上のアカウント フェデレーション サーバーの IP アドレスです。 自体にではなく、アカウント フェデレーション サーバーにホスト名 fs.fabrikam.com を解決するのには、アカウント フェデレーション サーバー プロキシにできるようになります: インターネット DNS を使用して fs.fabrikam.com を検索しようとした場合に発生すると、: フェデレーション サーバー プロキシは、フェデレーション サーバーと通信できるようにします。  
  
### <a name="2-configure-internet-dns"></a>2. インターネット DNS を構成する  
このシナリオで名前解決が正常に行われるためには、インターネット上のクライアント コンピューターから fs.fabrikam.com へのすべての要求が、ユーザーが制御するインターネット DNS ゾーンによって解決される必要があります。 そのため、境界ネットワーク内には、アカウント フェデレーション サーバー プロキシの IP アドレスに fs.fabrikam.com に対するクライアント要求を転送する、インターネット上の DNS ゾーンを構成する必要があります。  
  
境界ネットワークとインターネットの DNS ゾーンを変更する方法の詳細については、次を参照してください。 [DNS ゾーンことはどちらも、境界ネットワークとインターネット クライアントでのフェデレーション サーバー プロキシの名前解決を構成する](../../ad-fs/deployment/Configure-Name-Resolution-for-a-Federation-Server-Proxy-in-a-DNS-Zone-That-Serves-Both-the-Perimeter-Network-and-Internet-Clients.md)です。  
  
## <a name="see-also"></a>関連項目
[Windows Server 2012 で AD FS 設計ガイドします。](AD-FS-Design-Guide-in-Windows-Server-2012.md)