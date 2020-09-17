---
title: すべての必須の仮想スイッチ拡張機能が使用可能であることを確認する
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 2f2f2698-f5ec-4cad-aa64-d6987e8142a1
ms.date: 8/16/2016
ms.openlocfilehash: 8eeadf6ed8b90ef217d694e2f14b38314b8be7a5
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746857"
---
# <a name="ensure-that-all-mandatory-virtual-switch-extensions-are-available"></a>すべての必須の仮想スイッチ拡張機能が使用可能であることを確認する

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
*1つまたは複数の仮想ネットワークアダプターが、無効またはインストールされていない必須の拡張機能を持つ仮想スイッチに接続されています。*

## <a name="impact"></a>影響
*次の仮想マシン上の1つまたは複数の仮想ネットワークアダプターで、ネットワークトラフィックがブロックされています:*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*まず、必須の拡張機能がホストにインストールされていることを確認し、必要に応じて拡張機能をインストールします。その後、必須の拡張機能が無効になっている場合は、仮想スイッチマネージャーまたは Windows PowerShell コマンドレット VMSwitchExtension を使用して拡張機能を有効にします。*



