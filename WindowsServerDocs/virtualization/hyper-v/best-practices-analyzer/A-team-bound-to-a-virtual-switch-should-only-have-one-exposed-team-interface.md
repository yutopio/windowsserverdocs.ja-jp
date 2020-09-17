---
title: 仮想スイッチにバインドされたチームには、公開されているチームインターフェイスが1つだけ必要です
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 1074f086-1a2e-42e1-b58c-f55e657d5ce1
ms.date: 8/16/2016
ms.openlocfilehash: e600efe56c68f59ed8587e78a1d82576ff0c5c85
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746367"
---
# <a name="a-team-bound-to-a-virtual-switch-should-only-have-one-exposed-team-interface"></a>仮想スイッチにバインドされたチームには、公開されているチームインターフェイスが1つだけ必要です

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
*1つ以上の仮想スイッチが、複数のチームインターフェイスを持つチームにバインドされています。*

## <a name="impact"></a>影響
*次の仮想スイッチは、他のチームインターフェイスで使用されている Vlan および帯域幅にアクセスできない可能性があります。*

\<list of virtual switches>

## <a name="resolution"></a>解決策
*Windows PowerShell コマンドレット NetLbfoTeamNic を使用して、既定のチームインターフェイス以外のチームのすべてのチームインターフェイスを削除します。*



