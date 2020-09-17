---
title: このサーバーでの 1 つまたは複数の仮想マシンのレプリケーションが一時停止します。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: e1119a40-eda3-4058-8648-7df81cbc6c29
ms.date: 8/16/2016
ms.openlocfilehash: 3a2bf07e1f93aed3966dd98ce608af53168bdf9e
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746517"
---
# <a name="replication-is-paused-for-one-or-more-virtual-machines-on-this-server"></a>このサーバーでの 1 つまたは複数の仮想マシンのレプリケーションが一時停止します。

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
*1つまたは複数の仮想マシンのレプリケーションが一時停止しています。プライマリ仮想マシンが一時停止されている間に発生したすべての変更が累積され、レプリケーションが再開されるとレプリカ仮想マシンに送信されます。*

## <a name="impact"></a>影響
*レプリケーションが一時停止されている限り、プライマリ仮想マシンで発生した累積された変更によって、プライマリサーバー上の使用可能なディスク領域が消費されます。レプリケーションが再開されると、レプリカサーバーへのネットワークトラフィックが大量に発生する可能性があります。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*レプリケーションの一時停止が意図されていることを確認します。ディスク領域不足またはネットワーク接続に対処するためにレプリケーションが一時停止されている場合は、それらの問題が解決されるとすぐにレプリケーションを再開します。*



