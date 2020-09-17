---
title: ポート ミラーリングの宛先として 1 つまたは複数のネットワーク アダプターを構成する必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: b83c166d-f010-47c4-a4bb-02167f2e3361
ms.date: 8/16/2016
ms.openlocfilehash: cf1713bb6897f68c7bee839b4a3e4838aaa8a2fb
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745607"
---
# <a name="one-or-more-network-adapters-should-be-configured-as-the-destination-for-port-mirroring"></a>ポート ミラーリングの宛先として 1 つまたは複数のネットワーク アダプターを構成する必要があります。

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
*1 つまたは複数の仮想マシンのポート ミラーリングは、ソースとして構成されているネットワーク アダプターが、仮想スイッチ上の対応する送信先がないです。*

## <a name="impact"></a>**影響**
*ポート ミラーリングは、次の仮想スイッチと仮想マシンは正しく機能しません。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*完了するか、ポート ミラーリング構成を修正するには、Windows PowerShell または HYPER-V マネージャーを使用します。*



