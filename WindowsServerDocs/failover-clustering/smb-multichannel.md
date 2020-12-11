---
description: 簡略化された SMB マルチチャネルとマルチ NIC クラスターネットワークの詳細について説明します。
ms.assetid: a6343f1c-e9dd-4a02-91ad-39bd519d66cd
title: 簡略化された SMB マルチチャネルと複数 NIC のクラスター ネットワーク
ms.topic: article
author: RobHindman
ms.author: robhind
ms.date: 09/15/2016
ms.openlocfilehash: 537c5339505a57992c702d343bf9e130ced8d185
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97047240"
---
# <a name="simplified-smb-multichannel-and-multi-nic-cluster-networks"></a>簡略化された SMB マルチチャネルと複数 NIC のクラスター ネットワーク

> 適用先:Windows Server 2019、Windows Server 2016

簡略化された SMB マルチチャネルとマルチ<abbr title="ネットワーク インターフェイス カード">NIC</abbr> クラスターネットワークは、同じクラスターネットワークサブネット上で複数の Nic を使用できるようにし、SMB マルチチャネルを自動的に有効にする機能です。

簡略化された SMB マルチチャネルとマルチ NIC クラスターネットワークには、次のような利点があります。
- フェールオーバークラスタリングでは、同じスイッチ/同じサブネットを使用しているノード上のすべての Nic が自動的に認識されます。追加の構成は必要ありません。
- SMB マルチチャネルは自動的に有効になります。
- IPv6 リンクローカル (fe80) の IP アドレスリソースのみを持つネットワークは、クラスター専用 (プライベート) ネットワークで認識されます。
- 既定では、各クラスターアクセスポイント (CAP) のネットワーク名 (NN) に1つの IP アドレスリソースが構成されます。
- 同じサブネットに複数の Nic が存在する場合、クラスター検証で警告メッセージが発行されなくなりました。

## <a name="requirements"></a>要件
-   サーバーごとに複数の Nic。同じスイッチ/サブネットを使用します。

## <a name="how-to-take-advantage-of-multi-nic-clusters-networks-and-simplified-smb-multichannel"></a>マルチ NIC クラスターネットワークと簡略化された SMB マルチチャネルを活用する方法
このセクションでは、新しいマルチ NIC クラスターネットワークと簡略化された SMB マルチチャネル機能を活用する方法について説明します。

### <a name="use-at-least-two-networks-for-failover-clustering"></a>フェールオーバークラスタリングに2つ以上のネットワークを使用する
まれにもありますが、ネットワークスイッチが失敗する可能性があります。フェールオーバークラスタリングには、少なくとも2つのネットワークを使用することをお勧めします。 検出されたすべてのネットワークは、クラスターのハートビートに使用されます。 単一障害点を回避するために、フェールオーバークラスターに1つのネットワークを使用することは避けてください。 理想的には、クラスター内のノード間には複数の物理通信パスがあり、単一障害点はありません。

![フェールオーバークラスタリングのための2つのネットワークの図 ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig1.png)
 **1: フェールオーバークラスタリングに2つ以上のネットワークを使用する**

### <a name="use-multiple-nics-across-clusters"></a>クラスター間で複数の Nic を使用する

簡略化された SMB マルチチャネルの最大の利点は、複数の Nic がクラスター間で使用されている場合に、記憶域と記憶域の両方のワークロードクラスターで実現されます。 これにより、ワークロードクラスター (Hyper-v、SQL Server フェールオーバークラスターインスタンス、記憶域レプリカなど) で SMB マルチチャネルを使用できるようになり、ネットワークをより効率的に使用できるようになります。 スケールアウトファイルサーバークラスターを使用して Hyper-v または SQL Server フェールオーバークラスターインスタンスクラスターのワークロードデータを格納する、収束 (非集約) クラスター構成では、このネットワークは "North-South サブネット"/ネットワークと呼ばれることがよくあります。 多くのお客様は、RDMA 対応の NIC カードとスイッチに投資することで、このネットワークのスループットを最大化します。

![North-South SMB サブネットの図 ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig2.png)
 **2: 最大のネットワークスループットを実現するには、スケールアウトファイルサーバークラスターと、North-South サブネットを共有する hyper-v または SQL Server のフェールオーバークラスターインスタンスクラスターの両方で複数の nic を使用します。**

![SMB マルチチャネルを活用するために同じサブネット内の複数の Nic を使用する2つのクラスターのスクリーンショット ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig3.png)
 **図 3: 2 つのクラスター (記憶域のスケールアウトファイルサーバー SQL Server、 <abbr title=" "> ワークロード用のフェールオーバークラスタリングインスタンス fci) は、 </abbr> 同じサブネット内の複数の NIC を使用して smb マルチチャネルを活用し、ネットワークスループットを向上** させます

## <a name="automatic-recognition-of-ipv6-link-local-private-networks"></a>IPv6 リンクローカルプライベートネットワークの自動認識
複数の Nic を持つプライベート (クラスターのみ) ネットワークが検出されると、クラスターは各サブネットの各 NIC について、IPv6 リンクローカル (fe80) の IP アドレスを自動的に認識します。 これにより、管理者は IPv6 リンクローカル (fe80) の IP アドレスリソースを手動で構成する必要がなくなるため、管理者の時間を節約できます。

複数のプライベート (クラスターのみ) ネットワークを使用する場合は、IPv6 ルーティングの構成を確認して、ルーティングがサブネットを越えるように構成されていないことを確認します。これにより、ネットワークのパフォーマンスが低下します。

![フェールオーバークラスターマネージャー UI での自動ネットワーク構成のスクリーンショット ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig4.png)
 **図 4: 自動 IPv6 リンクローカル (Fe80) アドレスリソースの構成**

## <a name="throughput-and-fault-tolerance"></a>スループットとフォールトトレランス
Windows Server 2019 および Windows Server 2016 は自動的に NIC 機能を検出し、可能な限り最速の構成で各 NIC を使用しようとします。 チーミングされた Nic、RSS を使用した nic、および RDMA 機能を備えた nic のすべてを使用できます。 次の表は、これらのテクノロジを使用する場合のトレードオフの概要を示しています。 複数の RDMA 対応 Nic を使用する場合は、最大スループットが達成されます。 詳細については、「 [SMB マルチチャネルの基本](/archive/blogs/josebda/the-basics-of-smb-multichannel-a-feature-of-windows-server-2012-and-smb-3-0)」を参照してください。

![さまざまな NIC 構成のスループットとフォールトトレランスの図 ](media/Simplified-SMB-Multichannel-and-Multi-NIC-Cluster-Networks/Clustering_MulitNIC_Fig5.png)
 **5: さまざまな nic 構成のスループットとフォールトトレランス**

## <a name="frequently-asked-questions"></a>よく寄せられる質問
**マルチ NIC ネットワーク内のすべての Nic は、クラスターのハートビートに使用されますか。**
はい。

**マルチ NIC ネットワークはクラスター通信にのみ使用できますか。または、クライアントとクラスターの通信にのみ使用できますか。**
いずれの構成も機能します。すべてのクラスターネットワークの役割は、マルチ NIC ネットワークで動作します。

**SMB マルチチャネルは CSV およびクラスタートラフィックにも使用されますか。**
はい。既定では、すべてのクラスターおよび CSV トラフィックで、使用可能なマルチ NIC ネットワークが使用されます。 管理者は、フェールオーバークラスタリングの PowerShell コマンドレットまたはフェールオーバークラスターマネージャー UI を使用して、ネットワークの役割を変更できます。

**SMB マルチチャネルの設定を表示するにはどうすればよいですか。**
**SMBServerConfiguration** コマンドレットを使用して、 **EnableMultiChannel** プロパティの値を探します。

**クラスター共通プロパティは、マルチ NIC ネットワークで PlumbAllCrossSubnetRoutes 尊重されていますか。**
はい。

## <a name="additional-references"></a>その他の参照情報
- [Windows Server のフェールオーバー クラスタリングの新機能に関する記事](whats-new-in-failover-clustering.md)
