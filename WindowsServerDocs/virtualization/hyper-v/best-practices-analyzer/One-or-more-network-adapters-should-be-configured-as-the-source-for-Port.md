---
title: 1 つまたは複数のネットワーク アダプターは、ポート ミラーリングのソースとして構成する必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 147fd00f-1440-44d1-94e3-3a8af63aa7ed
ms.date: 8/16/2016
ms.openlocfilehash: c8a04001986ab4d3722c9e51a5d5ceb7cbd0bf02
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746247"
---
# <a name="one-or-more-network-adapters-should-be-configured-as-the-source-for-port-mirroring"></a>1 つまたは複数のネットワーク アダプターは、ポート ミラーリングのソースとして構成する必要があります。

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
*1 つまたは複数の仮想マシン ポート ミラーリングは、出力先として構成されたネットワーク アダプタが、仮想スイッチに対応するソースがないです。*

## <a name="impact"></a>**影響**
*ポート ミラーリングは、次の仮想スイッチと仮想マシンは正しく機能しません。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*完了するか、ポート ミラーリング構成を修正するには、Windows PowerShell または HYPER-V マネージャーを使用します。*



