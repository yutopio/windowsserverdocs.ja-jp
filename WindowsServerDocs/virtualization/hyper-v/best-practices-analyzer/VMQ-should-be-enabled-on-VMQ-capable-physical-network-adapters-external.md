---
title: 外部仮想スイッチにバインドされている VMQ 対応の物理ネットワーク アダプターで VMQ を有効にする必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 93d1b155-bf44-46b0-bb69-d34d5b30e574
ms.date: 8/16/2016
ms.openlocfilehash: 169f2ea06bf35c7bbc9bcaec354ca66e118c75d2
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746767"
---
# <a name="vmq-should-be-enabled-on-vmq-capable-physical-network-adapters-bound-to-an-external-virtual-switch"></a>外部仮想スイッチにバインドされている VMQ 対応の物理ネットワーク アダプターで VMQ を有効にする必要があります。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*次のネットワーク アダプターが仮想マシン キュー (VMQ) が、機能が無効になっています。*

## <a name="impact"></a>**影響**
*Windows では、活用するために使用できるハードウェア オフロードの次のネットワーク アダプターにできません。*

\<list of network adapters>

## <a name="resolution"></a>**解決方法**
*VMQ が有効にする NetAdapterVmq Windows PowerShell コマンドレットを使用して、またはネットワーク アダプターのプロパティの高度なユーザー インターフェイスを使用して有効にします。*



