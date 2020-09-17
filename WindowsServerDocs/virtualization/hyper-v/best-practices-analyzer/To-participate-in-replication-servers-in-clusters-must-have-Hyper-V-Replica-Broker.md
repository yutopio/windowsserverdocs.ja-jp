---
title: レプリケーションに参加するには、フェールオーバークラスター内のサーバーに Hyper-v レプリカブローカーが構成されている必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 5ec88ce5-a8b2-4ece-9062-366523c8b17f
ms.date: 8/16/2016
ms.openlocfilehash: 7fdd6167561be4922540a0def1f91f70b519aa0f
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746127"
---
# <a name="to-participate-in-replication-servers-in-failover-clusters-must-have-a-hyper-v-replica-broker-configured"></a>レプリケーションに参加するには、フェールオーバークラスター内のサーバーに Hyper-v レプリカブローカーが構成されている必要があります。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|エラー|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*フェールオーバークラスターの場合、Hyper-v レプリカでは、個々のサーバー名の代わりに Hyper-v レプリカブローカー名を使用する必要があります。*

## <a name="impact"></a>影響
*仮想マシンが別のフェールオーバークラスターノードに移動された場合、レプリケーションを続行できません。*

## <a name="resolution"></a>解決策
*フェールオーバークラスターマネージャーを使用して、Hyper-v レプリカブローカーを構成します。Hyper-v マネージャーで、レプリケーション構成で Hyper-v レプリカブローカー名がサーバー名として使用されていることを確認します。*



