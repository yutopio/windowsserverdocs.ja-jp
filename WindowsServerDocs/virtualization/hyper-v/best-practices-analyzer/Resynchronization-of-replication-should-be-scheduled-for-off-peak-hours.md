---
title: オフピーク時間にレプリケーションの再同期をスケジュールする必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 093a7bb7-8e0a-486b-b42b-04edd8809710
ms.date: 8/16/2016
ms.openlocfilehash: 97df7945988f117ed16d59685cc60841775737da
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746157"
---
# <a name="resynchronization-of-replication-should-be-scheduled-for-off-peak-hours"></a>オフピーク時間にレプリケーションの再同期をスケジュールする必要があります。

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
*プライマリ仮想マシンのレプリケーションの再同期は、オフピーク時の予定はありません。*

## <a name="impact"></a>影響
*仮想マシンの再同期が必要な状態が長くなるほど、レプリケーションログファイルが大きくなり、プライマリ仮想マシンでレプリケートされていない変更が増えることになります。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*HYPER-V マネージャーを使用すると、オフピーク時間中に自動的に再同期を実行するのに仮想マシンのレプリケーション設定を変更できます。*



