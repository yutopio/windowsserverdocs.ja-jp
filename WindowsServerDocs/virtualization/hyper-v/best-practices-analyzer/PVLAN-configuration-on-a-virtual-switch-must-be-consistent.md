---
title: 仮想スイッチ上 PVLAN 構成は、一貫性のあるである必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 4db63bcc-7a54-4f19-98a6-c274c3956d51
ms.date: 8/16/2016
ms.openlocfilehash: 205917e793bfb0cc398f7309981109083189d439
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745587"
---
# <a name="pvlan-configuration-on-a-virtual-switch-must-be-consistent"></a>仮想スイッチ上 PVLAN 構成は、一貫性のあるである必要があります。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|エラー|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*プライベート仮想ローカル エリア ネットワーク (PVLAN) は、1 つまたは複数の仮想ネットワーク アダプターで正しく構成されていません。*

## <a name="impact"></a>**影響**
*PVLAN では、仮想マシン間のネットワーク トラフィックを正しく特定可能性があります。*

## <a name="resolution"></a>**解決方法**
*PVLAN を正しく構成するのにには、Windows PowerShell コマンドレット、Set-vmnetworkadaptervlan を使用します。*



