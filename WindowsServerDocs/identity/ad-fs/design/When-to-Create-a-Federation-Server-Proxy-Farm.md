---
description: 詳細については、「フェデレーションサーバープロキシファームを作成する場合」を参照してください。
ms.assetid: ad0bf21d-2ace-4565-b1f5-ce57c8eb2689
title: フェデレーション サーバー プロキシ ファームを作成するのに適した状況
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 370c4c0b30357fb9216a8c89be96351e5054ad5c
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049330"
---
# <a name="when-to-create-a-federation-server-proxy-farm"></a>フェデレーション サーバー プロキシ ファームを作成するのに適した状況

大規模な Active Directory フェデレーションサービス (AD FS) \( AD FS 展開で、 \) プロキシ展開のフォールトトレランス、負荷 \- 分散、およびスケーラビリティを提供する場合は、追加のフェデレーションサーバープロキシをインストールすることを検討してください。 同じ境界ネットワーク内に複数のフェデレーションサーバープロキシを作成し、それぞれを同じ AD FS を保護するように構成するとフェデレーションサービスフェデレーションサーバープロキシファームが作成されます。

AD FS フェデレーションサーバープロキシ構成ウィザードを使用して、フェデレーションサーバープロキシファームを作成するか、既存のファームに追加のフェデレーションサーバープロキシをインストールすることができます。 詳細については、「 [When to Create a Federation Server Proxy](When-to-Create-a-Federation-Server-Proxy.md)」を参照してください。

すべてのフェデレーションサーバープロキシをファームとして機能させるには、まず、1つの IP アドレスと1つのドメインネームシステム \( DNS \) 完全修飾ドメイン名の FQDN でクラスターをクラスター化する必要があり \( \) ます。 サーバーをクラスター化するには、 \( 境界ネットワーク内に Microsoft ネットワーク負荷分散 NLB を展開し \) ます。 次の表のタスクでは、ファーム内のフェデレーションサーバープロキシをクラスター化するために NLB が適切に構成されている必要があります。

Microsoft NLB テクノロジを使用してクラスターの FQDN を構成する方法の詳細については、「 [クラスターパラメーターの指定](https://go.microsoft.com/fwlink/?linkid=74651)」を参照してください。

## <a name="configuring-federation-server-proxies-for-a-farm"></a>ファーム用のフェデレーション サーバー プロキシの構成
次の表では、各フェデレーションサーバープロキシがファームに参加できるようにするために完了する必要があるタスクについて説明します。

|タスク|説明|
|--------|---------------|
|ファーム内のすべてのプロキシが同じ AD FS フェデレーションサービス名を指すようにする|フェデレーションサーバープロキシを作成する場合は、ファームに参加するすべてのフェデレーションサーバープロキシに対して、AD FS フェデレーションサーバープロキシ構成ウィザードで同じフェデレーションサービス名を入力する必要があります。 フェデレーションサーバープロキシは、この DNS ホスト名を構成する URL を使用して、接続先の AD FS フェデレーションサービスインスタンスを決定します。<p>詳細については、「 [Configure a Computer for the Federation Server Proxy Role](../../ad-fs/deployment/Configure-a-Computer-for-the-Federation-Server-Proxy-Role.md)」を参照してください。|
|証明書を取得して共有する|パブリック証明機関 (VeriSign など) からサーバー認証証明書を取得 \( \) し、すべてのフェデレーションサーバープロキシが各フェデレーションサーバープロキシの既定の Web サイトで同じ証明書の同じ秘密キー部分を共有するように証明書を構成することができます。 証明書を共有するには、各フェデレーションサーバープロキシの既定の Web サイトに同じサーバー認証証明書をインストールする必要があります。 詳細については、「 [サーバー認証証明書を既定の Web サイトにインポートする](../../ad-fs/deployment/Import-a-Server-Authentication-Certificate-to-the-Default-Web-Site.md)」を参照してください。<p>詳細については、「 [Certificate Requirements for Federation Server Proxies](Certificate-Requirements-for-Federation-Server-Proxies.md)」を参照してください。|

フェデレーションサーバープロキシファームを作成するために新しいフェデレーションサーバープロキシを追加する方法の詳細については、「 [チェックリスト: フェデレーションサーバープロキシの](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server-Proxy.md)セットアップ」を参照してください。

## <a name="see-also"></a>関連項目
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
