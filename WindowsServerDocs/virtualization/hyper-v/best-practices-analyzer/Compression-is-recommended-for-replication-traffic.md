---
title: レプリケーショントラフィックには圧縮を使用することをお勧めします
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: cf8be6e9-2909-4e4a-bb63-d1e1ebbc6930
ms.date: 8/16/2016
ms.openlocfilehash: 61f1b56720af3583745960073823fef7b7b5173f
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745847"
---
# <a name="compression-is-recommended-for-replication-traffic"></a>レプリケーショントラフィックには圧縮を使用することをお勧めします

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*ネットワーク経由でプライマリサーバーからレプリカサーバーに送信されるレプリケーショントラフィックは圧縮されていません。*

## <a name="impact"></a>影響
*レプリケーショントラフィックでは、必要以上の帯域幅が使用されます。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*Hyper-v マネージャーで、仮想マシンの設定でネットワーク経由で転送されるデータを圧縮するように Hyper-v レプリカを構成します。また、Hyper-v の外部でツールを使用して圧縮を行うこともできます。*



