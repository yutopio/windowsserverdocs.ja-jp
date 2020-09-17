---
title: 動的仮想ハードディスクまたは差分ディスク上の仮想ブロックと物理ディスクセクター間のアラインメントの不整合を回避する
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: a17c8fd2-af81-485b-bfea-bd1ef3e43923
ms.date: 8/16/2016
ms.openlocfilehash: aa165dad38ae455f7c4a5a0d73cdd005c01a60ef
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90747097"
---
# <a name="avoid-alignment-inconsistencies-between-virtual-blocks-and-physical-disk-sectors-on-dynamic-virtual-hard-disks-or-differencing-disks"></a>動的仮想ハードディスクまたは差分ディスク上の仮想ブロックと物理ディスクセクター間のアラインメントの不整合を回避する

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
*1つまたは複数のバーチャルハードディスクのアラインメントの不整合が検出されました。*

### <a name="impact"></a>影響
*バーチャルハードディスクがセクターサイズ4K の物理ディスクに格納されている場合、バーチャルハードディスクを使用するバーチャルマシンまたはアプリケーションでパフォーマンスの問題が発生する可能性があります。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*バーチャルハードディスクの作成ウィザードを使用して、新しい VHD 形式または VHDX 形式のバーチャルハードディスクを作成し、既存のバーチャルハードディスクをソースディスクとして指定します。新しい仮想ハードディスクは、仮想ブロックと物理ディスクの間に配置されます。*



