---
title: バーチャルマシンで差分バーチャルハードディスクを使用する場合は、十分な物理ディスク領域が使用可能であることを確認します。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 71f99aab-f994-4022-9da0-d661965b95ac
ms.date: 8/16/2016
ms.openlocfilehash: d5a8c5d38aa47845a88077eaa6b785dc5ebb148c
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746277"
---
# <a name="ensure-sufficient-physical-disk-space-is-available-when-virtual-machines-use-differencing-virtual-hard-disks"></a>バーチャルマシンで差分バーチャルハードディスクを使用する場合は、十分な物理ディスク領域が使用可能であることを確認します。

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
*1つ以上のバーチャルマシンで差分バーチャルハードディスクが使用されています。*

## <a name="impact"></a>影響
*差分仮想ハードディスクでは、仮想ハードディスクへの書き込みが発生したときに領域を割り当てることができるように、ホストボリュームに使用可能な領域が必要です。使用可能な領域が不足している場合は、物理記憶域に依存しているすべての仮想マシンが影響を受ける可能性があります。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*使用可能なディスク領域を監視して、仮想ハードディスクの拡張に十分な領域があることを確認します。差分仮想ハードディスクをその親にマージすることを検討してください。Hyper-v マネージャーで、差分ディスクを調べて親バーチャルハードディスクを特定します。差分ディスクを他の差分ディスクで共有されている親ディスクにマージすると、その操作によって、他の差分ディスクと親ディスクとの間の関係が破損し、使用できなくなります。親バーチャルハードディスクが共有されていないことを確認したら、ディスクの編集ウィザードを使用して、差分ディスクを親バーチャルハードディスクにマージできます。*



