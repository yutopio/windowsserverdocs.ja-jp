---
title: 初期レプリケーションが完了後は、テスト フェールオーバーを実行しようとする必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: cea7eeaa-c1a7-4f87-89be-d4e1208c546f
ms.date: 8/16/2016
ms.openlocfilehash: b41cd79ccbf0d04825d077da34e894fc9a17b10d
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746697"
---
# <a name="test-failover-should-be-attempted-after-initial-replication-is-complete"></a>初期レプリケーションが完了後は、テスト フェールオーバーを実行しようとする必要があります。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|操作|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="problem"></a>問題
*なかったテスト フェールオーバーには、少なくとも 1 か月です。*

## <a name="impact"></a>影響
*計画済みまたは計画外のフェールオーバーが成功するか、フェールオーバー後にワークロード操作が正常に続行されるかを確認するメッセージは表示されません。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*HYPER-V マネージャーを使用すると、テスト フェールオーバーを実行します。*



