---
title: フェールオーバー後に回復スナップショットを削除する必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 922115fa-e8dd-4055-aaf1-4a4437c5cf28
ms.date: 8/16/2016
ms.openlocfilehash: b30dbf9996f2406e3d260c825dbe2dbbc6918324
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745547"
---
# <a name="recovery-snapshots-should-be-removed-after-failover"></a>フェールオーバー後に回復スナップショットを削除する必要があります。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|操作|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*仮想マシンのフェールオーバーを持つ 1 つまたは複数の復旧スナップショットです。*

## <a name="impact"></a>**影響**
*使用可能な領域は、スナップショットファイルが格納されている物理ディスク上で実行される可能性があります。これが発生した場合は、物理記憶域に対して追加のディスク操作を実行することはできません。物理記憶域に依存しているすべての仮想マシンが影響を受ける可能性があります。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*仮想マシンがフェールオーバーごとには、回復スナップショットを削除し、フェールオーバーの完了を示す Windows PowerShell で Complete-vmfailover コマンドレットを使用します。*



