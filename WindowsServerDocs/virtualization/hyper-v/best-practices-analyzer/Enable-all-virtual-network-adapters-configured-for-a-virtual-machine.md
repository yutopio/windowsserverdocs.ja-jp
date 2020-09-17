---
title: 仮想マシンに構成されているすべての仮想ネットワークアダプターを有効にする
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: fcd350b7-4240-4359-aadd-93e7ac4d314e
ms.date: 8/16/2016
ms.openlocfilehash: 81e0bbb8fce32b8343a13dea953498efb627d496
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746287"
---
# <a name="enable-all-virtual-network-adapters-configured-for-a-virtual-machine"></a>仮想マシンに構成されているすべての仮想ネットワークアダプターを有効にする

>適用先:Windows Server 2016

ベスト プラクティスとスキャンの詳細については、「 [ベスト プラクティス アナライザー](https://go.microsoft.com/fwlink/?LinkId=122786)」をご覧ください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*1つまたは複数のネットワークアダプターがバーチャルマシンで無効になっている可能性があります。*

## <a name="impact"></a>影響

*次の仮想マシンがネットワークに接続されていない可能性があります。*

\<list of virtual machine names>

## <a name="resolution"></a>解決策

*ゲストオペレーティングシステムのデバイスマネージャーを使用して、すべての仮想ネットワークアダプターを有効にします。アダプターが不要な場合は、Hyper-v マネージャーを使用して仮想マシンから削除します。*



