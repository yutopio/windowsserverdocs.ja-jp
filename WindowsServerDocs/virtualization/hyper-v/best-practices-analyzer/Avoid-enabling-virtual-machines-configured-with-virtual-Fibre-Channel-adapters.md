---
title: 仮想ファイバーチャネルアダプターで構成された仮想マシンが、コピー先のファイバーチャネル論理ユニット (Lun) へのパスがソースよりも小さい場合にライブマイグレーションを実行できるようにしない
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.date: 8/16/2016
ms.openlocfilehash: 71617bbf6718e77f004b57e38035f5277c45c3bc
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90747067"
---
# <a name="avoid-enabling-virtual-machines-configured-with-virtual-fibre-channel-adapters-to-allow-live-migrations-when-there-are-fewer-paths-to-fibre-channel-logical-units-luns-on-the-destination-than-on-the-source"></a>仮想ファイバーチャネルアダプターで構成された仮想マシンが、コピー先のファイバーチャネル論理ユニット (Lun) へのパスがソースよりも小さい場合にライブマイグレーションを実行できるようにしない

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
*1つ以上の仮想マシンで、仮想化 WMI プロバイダーに AllowReducedFcRedunancy プロパティが設定されています。*

## <a name="impact"></a>**影響**
*次の仮想マシンのライブマイグレーションにより、データが失われたり、記憶域への i/o が中断されることがあります。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*影響を受ける仮想マシンで AllowReducedFcRedundancy WMI プロパティをクリアすることを検討してください。このプロパティをオフにすると、仮想ファイバーチャネルアダプターが構成されている仮想マシンでライブマイグレーションを実行できるのは、移行先でファイバーチャネルするパスの数が、ソースのパスの数と同じか、それよりも多い場合のみです。これらのチェックにより、データの損失や記憶域への i/o の中断を防ぐことができます。*