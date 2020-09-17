---
title: 仮想 SAN は、物理ホストバスアダプターに関連付けられている必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 14bca69b-e779-4e90-b5c1-1b015625572f
ms.date: 8/16/2016
ms.openlocfilehash: d49cbedb76320f3c1967bfd6cfd1e9590fd8925d
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746377"
---
# <a name="a-virtual-san-should-be-associated-with-a-physical-host-bus-adapter"></a>仮想 SAN は、物理ホストバスアダプターに関連付けられている必要があります。

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
*ホストバスアダプター (HBA) に関連付けられていない仮想記憶域エリアネットワーク (SAN) が構成されています。*

## <a name="impact"></a>**影響**
*構成が正しくない仮想 SAN に接続された仮想ファイバーチャネルアダプターを使用して構成されている場合、仮想マシンは起動しません。これは、次の仮想 San に影響します。*


\<list of virtual SANs>


## <a name="resolution"></a>**解決方法**
*ホストバスアダプターに接続して、仮想 SAN を再構成します。*





