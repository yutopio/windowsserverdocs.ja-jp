---
title: シリアル ポートが第 2 世代仮想マシンで構成します。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 87061193-dd3f-4398-aa5d-4cee83cadfa3
ms.date: 8/16/2016
ms.openlocfilehash: 2dbb9aae488922daeff74242d74d38685a371497
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90744107"
---
# <a name="serial-ports-should-not-be-configured-on-generation-2-virtual-machines"></a>シリアル ポートが第 2 世代仮想マシンで構成します。

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
*1 つまたは複数の世代 2 の仮想マシンでは、構成されているシリアル ポートがあります。*

## <a name="impact"></a>**影響**
*次の仮想マシンのパフォーマンスに影響する可能性があります。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*これが意図的なものである場合は、それ以上の操作は必要ありません。それ以外の場合は、Hyper-v マネージャーまたは Windows PowerShell を使用して、仮想マシンのシリアルポートから接続文字列を削除することを検討してください。*



