---
title: 使用可能な場合は、ネットワークにすべての仮想機能を使用する
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: bf895484-6a0d-4aa4-9a42-9fac739e875d
ms.date: 8/16/2016
ms.openlocfilehash: 4a1502180350c338793bf811cddc675785e9c67a
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746807"
---
# <a name="use-all-virtual-functions-for-networking-when-they-are-available"></a>使用可能な場合は、ネットワークにすべての仮想機能を使用する

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
*一部のハードウェアアクセラレータ機能が使用されていません*

## <a name="impact"></a>影響
*この構成によって、全体的な CPU 使用率が必要以上に高くなる可能性があります。次の仮想マシンでは、ネットワークのパフォーマンスが最適ではない可能性があります。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*物理ハードウェアが sr-iov をサポートし、この構成が仮想マシンに必要なネットワーク機能と競合しない場合は、sr-iov 用の仮想ネットワークアダプターを構成することを検討してください。*



