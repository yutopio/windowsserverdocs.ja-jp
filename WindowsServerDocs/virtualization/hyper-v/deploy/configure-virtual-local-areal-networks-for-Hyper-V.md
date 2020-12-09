---
title: Hyper-v の仮想ローカルエリアネットワークを構成する
description: Hyper-v ホスト上のバーチャルマシンで使用する仮想ローカルエリアネットワーク (VLAN) を構成する手順について説明します。
ms.topic: article
ms.assetid: 8510a709-001c-4eee-b6d6-c451e8a8a836
ms.author: benarm
author: BenjaminArmstrong
ms.date: 10/11/2016
ms.openlocfilehash: 22f9890fd1a3a90fcbab59a9ed1de8481e117e75
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96866161"
---
# <a name="configure-virtual-local-area-networks-for-hyper-v"></a>Hyper-v の仮想ローカルエリアネットワークを構成する
仮想ローカルエリアネットワーク \( vlan \) は、ネットワークトラフィックを分離するための1つの方法を提供します。 Vlan は、802.1 q をサポートするスイッチとルーターで構成されます。 複数の Vlan を構成し、それらの間で通信が行われるようにするには、ネットワークデバイスでそのような構成を行う必要があります。

Vlan を構成するには、次のものが必要です。

- 802.1 q VLAN タグ付けをサポートする物理ネットワークアダプターとドライバー。
- 802.1 q VLAN タグ付けをサポートする物理ネットワークスイッチ。

ホストでは、物理スイッチポートのネットワークトラフィックを許可するように仮想スイッチを構成します。 これは、仮想マシンで内部的に使用する VLAN Id を対象としています。 次に、仮想マシンがすべてのネットワーク通信に使用する VLAN を指定するように、仮想マシンを構成します。

#### <a name="to-allow-a-virtual-switch-to-use-a-vlan"></a>仮想スイッチで VLAN を使用できるようにするには

1. Hyper-v \- マネージャーを開きます。

2. [操作] メニューの **[仮想スイッチ マネージャー]** をクリックします。

3. [ **仮想スイッチ**] で、vlan をサポートする物理ネットワークアダプターに接続されている仮想スイッチを選択します。

4. 右側のウィンドウの [VLAN ID] で、[ **仮想 LAN の識別を有効にする** ] を選択し、vlan id の番号を入力します。

    仮想スイッチに接続されている物理ネットワークアダプターを経由するすべてのトラフィックには、設定した VLAN ID がタグ付けされます。

#### <a name="to-allow-a-virtual-machine-to-use-a-vlan"></a>バーチャルマシンで VLAN を使用できるようにするには

1. Hyper-v \- マネージャーを開きます。

2. 結果ウィンドウの [ **Virtual Machines** で、適切な仮想マシンを選択し、[ **設定**] を右クリックします。

3. [ **ハードウェア**] で、VLAN が設定されている仮想スイッチを選択します。

4. 右側のウィンドウで、[ **仮想 LAN の識別を有効にする**] を選択し、仮想スイッチに指定したものと同じ VLAN ID を入力します。

仮想マシンでより多くの Vlan を使用する必要がある場合は、次のいずれかの操作を行います。

- より多くの仮想ネットワークアダプターを適切な仮想スイッチに接続し、VLAN Id を割り当てます。 IP アドレスが正しく構成されていること、および VLAN 経由でルーティングするトラフィックにも正しい IP アドレスが使用されていることを確認してください。

- [Set \- set-vmnetworkadaptervlan](/powershell/module/hyper-v/set-vmnetworkadaptervlan)コマンドレットを使用して、仮想ネットワークアダプターをトランクモードで構成します。

## <a name="see-also"></a>関連項目

[Hyper-v \- 仮想スイッチ](../../hyper-v-virtual-switch/hyper-v-virtual-switch.md)
