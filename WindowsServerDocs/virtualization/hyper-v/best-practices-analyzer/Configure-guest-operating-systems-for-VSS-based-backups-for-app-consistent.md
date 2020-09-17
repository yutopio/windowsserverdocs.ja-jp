---
title: VSS ベースのバックアップ用のゲストオペレーティングシステムを構成して、Hyper-v レプリカのアプリケーション整合性スナップショットを有効にする
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 7638e996-d42d-47b8-a670-1e09e7183850
ms.date: 8/16/2016
ms.openlocfilehash: b6a7eec504282e63e0cb24efbd2cdc5f66849005
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746887"
---
# <a name="configure-guest-operating-systems-for-vss-based-backups-to-enable-application-consistent-snapshots-for-hyper-v-replica"></a>VSS ベースのバックアップ用のゲストオペレーティングシステムを構成して、Hyper-v レプリカのアプリケーション整合性スナップショットを有効にする

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|エラー|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*アプリケーション整合性スナップショットを使用するには、レプリケーションに参加している仮想マシンのゲストオペレーティングシステムで、ボリュームシャドウコピーサービス (VSS) が有効になっていて構成されている必要があります。*

## <a name="impact"></a>影響
*レプリケーション構成でアプリケーション整合性スナップショットが指定されている場合でも、VSS が構成されていないと、Hyper-v はそれらを使用しません。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*仮想マシン接続を使用すると、仮想マシンで統合サービスをインストールできます。*



