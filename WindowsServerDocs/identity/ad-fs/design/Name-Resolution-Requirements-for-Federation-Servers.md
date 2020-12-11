---
description: 詳細については、「フェデレーションサーバーの名前解決の要件」を参照してください。
ms.assetid: 74ef34c8-e13f-499b-b2bb-952ad7036622
title: フェデレーション サーバーの名前解決の要件
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 7f2946bedbbbc4677c65f594ea4967b4f5e4fdb3
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97046490"
---
# <a name="name-resolution-requirements-for-federation-servers"></a>フェデレーション サーバーの名前解決の要件

企業ネットワーク上のクライアント コンピューターがアプリケーションまたは Active Directory フェデレーション サービスによって保護されている Web サービスにアクセスしようとした場合に \(AD FS\), 、最初のフェデレーション サーバーを認証する必要があります。 認証する方法の 1 つでは、会社のネットワーク クライアントが Windows 統合認証を通じて、ローカルのフェデレーション サーバーにアクセスします。

## <a name="configure-corporate-dns"></a>企業 DNS を構成する
ローカルのフェデレーション サーバーで Windows 統合認証を通じて正常な名前解決を実行、ドメイン ネーム システム \(DNS\) アカウントの企業ネットワーク内には、新しいホストのパートナーを構成 \(A\) 完全修飾ドメイン名を解決するリソース レコード \(FQDN\) フェデレーション サーバー クラスターの IP アドレスにフェデレーション サーバーのホスト名です。

次の図を見ると、特定のシナリオでのこのタスクの実現方法がわかります。 この場合は、Microsoft Network Load Balancing \(NLB\) 既存のフェデレーション サーバー ファームの 1 つのクラスターの FQDN 名と 1 つのクラスター IP アドレスを提供します。

![名の要件](media/adfs2_deploy_single_fs.gif)

NLB を使用する FQDN をクラスターまたはクラスターの IP アドレスを構成する方法については、次を参照してください。 [クラスター パラメーターを指定して](https://go.microsoft.com/fwlink/?LinkId=75282)します。

会社の DNS にフェデレーション サーバーを構成する方法については、次を参照してください [ホストと #40; を追加します。。(&) #41 です。フェデレーション サーバー用の会社の DNS リソース レコード](../../ad-fs/deployment/Add-a-Host--A--Resource-Record-to-Corporate-DNS-for-a-Federation-Server.md)します。

境界ネットワーク内のフェデレーション サーバー プロキシを構成する方法については、次を参照してください。 [フェデレーション サーバー プロキシの名前解決要件](Name-Resolution-Requirements-for-Federation-Server-Proxies.md)します。


## <a name="see-also"></a>関連項目
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
