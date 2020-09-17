---
title: 親と子のバーチャルハードディスクが異なるボリュームにある場合に差分バーチャルハードディスクを使用すると、記憶域のサービスの品質を有効にしない
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: aa9ed408-65cf-40dc-aad2-118b54c70179
ms.date: 8/16/2016
ms.openlocfilehash: 792ee7f84694171b7b44602c8bb1a5c307d80c6c
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90747077"
---
# <a name="avoid-enabling-storage-quality-of-service-when-using-a-differencing-virtual-hard-disk-when-the-parent-and-child-virtual-hard-disks-are-on-different-volumes"></a>親と子のバーチャルハードディスクが異なるボリュームにある場合に差分バーチャルハードディスクを使用すると、記憶域のサービスの品質を有効にしない

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
*異なるボリューム上の親および子のバーチャルハードディスクを持つ差分バーチャルハードディスクで、記憶域のサービスの品質が有効になっています。*

## <a name="impact"></a>**影響**
*この構成では、差分仮想ハードディスクと、親ボリュームおよび子ボリューム上のその他の仮想ハードディスクに、予期しない記憶域のサービス品質の動作が発生する可能性があります。これは、次の仮想ハードディスクに影響します。*

\<list of virtual hard disks>

## <a name="resolution"></a>**解決方法**
*参照されるバーチャルハードディスク上の記憶域のサービス品質を無効にするか、記憶域の移行を実行して親と子の仮想ハードディスクを同じボリュームに移動してください。*



