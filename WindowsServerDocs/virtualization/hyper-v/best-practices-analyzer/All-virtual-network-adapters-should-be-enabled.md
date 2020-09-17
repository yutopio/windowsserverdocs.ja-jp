---
title: すべての仮想ネットワークアダプターを有効にする必要があります
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: b17d647d-a34a-44de-ada6-01a2bf5eeb48
ms.date: 8/16/2016
ms.openlocfilehash: 48417108f780c8b145613b110bb51681bd69bdc6
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746307"
---
# <a name="all-virtual-network-adapters-should-be-enabled"></a>すべての仮想ネットワークアダプターを有効にする必要があります

>適用先:Windows Server 2016



|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*物理ネットワークアダプターに関連付けられている1つまたは複数の仮想ネットワークアダプターが、管理オペレーティングシステムで無効になっています。*

## <a name="impact"></a>影響

*このサーバーの構成は最適ではありません。*

管理オペレーティングシステムは、無効な仮想ネットワークアダプターに関連付けられているため、このコンピューターの物理ネットワークアダプターのいずれかを使用して物理 (外部) ネットワークに接続することはできません。

## <a name="resolution"></a>解決策

*ネットワーク & のインターネット設定を使用して、仮想ネットワークアダプターを有効にします。または、仮想スイッチマネージャーを使用して、外部仮想スイッチが管理オペレーティングシステムと共有されないように再構成します。*



