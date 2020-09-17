---
title: 1 つ以上のネットワーク アダプターを使用する必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 59940e56-e06a-490f-90ea-cf30d9f80b09
ms.date: 8/16/2016
ms.openlocfilehash: 05dc0583424ed155c4780f9f0b4c016be850a71c
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746267"
---
# <a name="more-than-one-network-adapter-should-be-available"></a>1 つ以上のネットワーク アダプターを使用する必要があります。

>適用先:Windows Server 2016

ベスト プラクティスとスキャンの詳細については、「 [ベスト プラクティス アナライザー](https://go.microsoft.com/fwlink/?LinkId=122786)」をご覧ください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|エラー|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*管理オペレーティング システムで共有する 1 つのネットワーク アダプターと物理ネットワークへのアクセスを必要とするすべての仮想マシンでは、このサーバーを構成します。*

## <a name="impact"></a>影響

*管理オペレーティング システムのネットワークのパフォーマンスが低下する可能性があります。*

## <a name="resolution"></a>解決策

*このコンピューターにネットワークアダプターを追加します。管理オペレーティングシステムで使用するために1つのネットワークアダプターを予約するには、外部仮想ネットワークで使用するように構成しないでください。*

コンピューターにネットワーク アダプターを追加する方法の詳細については、コンピューターまたはネットワーク アダプターのドキュメントを参照してください。 次に、管理オペレーティング システム専用に予約する接続しないでください仮想スイッチにします。



