---
title: テスト フェールオーバーの実行には、少なくとも毎月フェールオーバーが成功し、フェールオーバー後に予期した仮想マシンのワークロードとして動作することを確認するには
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 57a8aa50-e59e-4a4b-8571-1099d5a8eee4
ms.date: 8/16/2016
ms.openlocfilehash: 4ec97d55f1a6caf33b1b46d0a6bdb4e99005c971
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90744095"
---
# <a name="test-failovers-should-be-carried-out-at-least-monthly-to-verify-that-failover-will-succeed-and-that-virtual-machine-workloads-will-operate-as-expected-after-failover"></a>テスト フェールオーバーの実行には、少なくとも毎月フェールオーバーが成功し、フェールオーバー後に予期した仮想マシンのワークロードとして動作することを確認するには

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|操作|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*なかったテスト フェールオーバーには、少なくとも 1 か月です。*

## <a name="impact"></a>影響
*計画済みまたは計画外のフェールオーバーが成功するか、フェールオーバー後にワークロード操作が正常に続行されるかを確認するメッセージは表示されません。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*HYPER-V マネージャーを使用すると、テスト フェールオーバーを実行します。*



