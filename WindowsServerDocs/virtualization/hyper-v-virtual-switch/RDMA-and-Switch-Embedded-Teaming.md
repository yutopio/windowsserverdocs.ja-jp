---
title: リモート ダイレクト メモリ アクセス (RDMA) とスイッチ埋め込みチーミング (SET)
description: このトピックでは、スイッチ埋め込みチーミング (SET) に関する情報に加え、Windows Server 2016 の Hyper-v を使用したリモートダイレクトメモリアクセス (RDMA) インターフェイスの構成について説明します。
manager: brianlic
ms.topic: get-started-article
ms.assetid: 68c35b64-4d24-42be-90c9-184f2b5f19be
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 9b8d1470b3e146625d794697231291c1f8156402
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96866191"
---
# <a name="remote-direct-memory-access-rdma-and-switch-embedded-teaming-set"></a>リモートダイレクトメモリアクセス \( RDMA \) およびスイッチ埋め込みチーミング \( セット\)

>適用先:Windows Server (半期チャネル)、Windows Server 2016

このトピックでは \( \) 、スイッチ埋め込みチーミングセットに関する情報に加えて、Windows Server 2016 の hyper-v を使用したリモートダイレクトメモリアクセス RDMA インターフェイスの構成について説明 \( \) します。

> [!NOTE]
> このトピックに加えて、次のスイッチ埋め込みチーミングコンテンツを使用できます。
> - TechNet ギャラリーのダウンロード: [Windows Server 2016 NIC とスイッチ Embedded チーミングユーザーガイド](https://gallery.technet.microsoft.com/Windows-Server-2016-839cb607?redir=0)

## <a name="configuring-rdma-interfaces-with-hyper-v"></a><a name="bkmk_rdma"></a>Hyper V と RDMA インターフェイスを構成します。

Windows Server 2012 R2 では、RDMA サービスが HYPER-V 仮想スイッチにバインドされていないことができますを提供するネットワーク アダプターと同じコンピューターに RDMA と HYPER-V の両方を使用します。 これにより、HYPER-V ホストにインストールするために必要な物理ネットワーク アダプターの数が増加します。

>[!TIP]
>Windows Server 2016 より前の Windows Server のエディションでは、NIC チームまたは Hyper-v 仮想スイッチにバインドされているネットワークアダプターで RDMA を構成することはできません。 Windows Server 2016 では、Hyper-v 仮想スイッチにバインドされているネットワークアダプターで RDMA を有効にすることができます (設定なし)。

Windows Server 2016 では、セットの有無、RDMA を使用しているときに以下のネットワーク アダプターを使用できます。

次の図は、Windows Server 2012 R2 と Windows Server 2016 の間でのソフトウェア アーキテクチャの変更を示しています。

![アーキテクチャの変更](../media/RDMA-and-SET/rdma_over.jpg)

以下のセクションでは、Windows PowerShell コマンドを使用してデータセンターブリッジング (DCB) を有効にする方法、RDMA 仮想 NIC vNIC を使用して Hyper-v 仮想スイッチを作成する方法、 \( \) およびセットと RDMA vnics を使用して Hyper-v 仮想スイッチを作成する方法について説明します。

### <a name="enable-data-center-bridging-dcb"></a>データセンターブリッジング DCB を有効にする \(\)

Rdma の集約型イーサネット roce バージョンを使用する前に \( \) 、DCB を有効にする必要があります。  インターネットワイドエリア RDMA プロトコルの iwarp ネットワークには必要ありません \( \) が、テストでは、イーサネットベースの rdma テクノロジがすべて DCB で動作しやすくなっていると判断しました。 このため、DCB を使用して、iWARP RDMA の展開についても検討してください。

次の Windows PowerShell コマンド例では、SMB ダイレクト用に DCB を有効にして構成する方法を示します。

DCB を有効にする

```powershell
Install-WindowsFeature Data-Center-Bridging
```

SMB ダイレクトのポリシーを設定します。

```powershell
New-NetQosPolicy "SMB" -NetDirectPortMatchCondition 445 -PriorityValue8021Action 3
```

SMB のフロー制御を有効にする:

```powershell
Enable-NetQosFlowControl  -Priority 3
```

他のトラフィックのフロー制御が無効になっていることを確認します。

```powershell
Disable-NetQosFlowControl  -Priority 0,1,2,4,5,6,7
```

ターゲットアダプターにポリシーを適用します。

```powershell
Enable-NetAdapterQos  -Name "SLOT 2"
```

SMB ダイレクトに帯域幅の最小30% を指定する:

```powershell
New-NetQosTrafficClass "SMB"  -Priority 3  -BandwidthPercentage 30  -Algorithm ETS
```

カーネル デバッガーがシステムにインストールした場合は、QoS では、次のコマンドを実行して設定を許可するようにデバッガーを構成する必要があります。

デバッガーのオーバーライド-既定では、デバッガーは NetQos をブロックします。

```powershell
Set-ItemProperty HKLM:"\SYSTEM\CurrentControlSet\Services\NDIS\Parameters" AllowFlowControlUnderDebugger -type DWORD -Value 1 -Force
```

### <a name="create-a-hyper-v-virtual-switch-with-an-rdma-vnic"></a>RDMA vNIC での HYPER-V 仮想スイッチの作成します。

設定が展開に必要ない場合は、次の Windows PowerShell コマンドを使用して、RDMA vNIC で Hyper-v 仮想スイッチを作成できます。

> [!NOTE]
> チームのセットを使用して、RDMA 対応の物理 Nic を持つ消費 Vnic の他の RDMA リソースを提供します。

```powershell
New-VMSwitch -Name RDMAswitch -NetAdapterName "SLOT 2"
```

ホスト vNICs を追加し、RDMA 対応にします。

```powershell
Add-VMNetworkAdapter -SwitchName RDMAswitch -Name SMB_1
Enable-NetAdapterRDMA "vEthernet (SMB_1)" "SLOT 2"
```
RDMA 機能を確認します。

```powershell
Get-NetAdapterRdma
```

###  <a name="create-a-hyper-v-virtual-switch-with-set-and-rdma-vnics"></a><a name="bkmk_set-rdma"></a>セットと RDMA Vnic で HYPER-V 仮想スイッチを作成します。

RDMA チーミングをサポートする Hyper-v 仮想スイッチ上の Hyper-v ホスト仮想ネットワークアダプター vnics で RDMA クローラーを使用するに \( \) は、次の例の Windows PowerShell コマンドを使用できます。

```powershell
New-VMSwitch -Name SETswitch -NetAdapterName "SLOT 2","SLOT 3" -EnableEmbeddedTeaming $true
```

ホスト vNICs の追加:

```powershell
Add-VMNetworkAdapter -SwitchName SETswitch -Name SMB_1 -managementOS
Add-VMNetworkAdapter -SwitchName SETswitch -Name SMB_2 -managementOS
```

多くのスイッチでは、タグなしの VLAN トラフィックにトラフィッククラスの情報が渡されないため、RDMA のホストアダプターが Vlan 上にあることを確認してください。 この例では、2つの SMB_ * ホスト仮想アダプターを VLAN 42 に割り当てます。

```powershell
Set-VMNetworkAdapterIsolation -ManagementOS -VMNetworkAdapterName SMB_1  -IsolationMode VLAN -DefaultIsolationID 42
Set-VMNetworkAdapterIsolation -ManagementOS -VMNetworkAdapterName SMB_2  -IsolationMode VLAN -DefaultIsolationID 42
```

ホスト vNICs で RDMA を有効にする:

```powershell
Enable-NetAdapterRDMA "vEthernet (SMB_1)","vEthernet (SMB_2)" "SLOT 2", "SLOT 3"
```

RDMA 機能を確認します。機能が0以外であることを確認します。

```powershell
Get-NetAdapterRdma | fl *
```

## <a name="switch-embedded-teaming-set"></a>スイッチが埋め込まれたチーミング (設定)

このセクションでは、Windows Server 2016 のスイッチ埋め込みチーミング (SET) の概要について説明します。次のセクションが含まれています。

- [セットの概要](#bkmk_over)

- [セットの可用性](#bkmk_avail)

- [セットのサポート対象およびサポート非対象の Nic](#bkmk_nics)

- [Windows Server ネットワーク テクノロジとの互換性を設定します。](#bkmk_compat)

- [セットのモードと設定](#bkmk_modes)

- [セットと仮想マシン キュー (VMQs)](#bkmk_vmq)

- [セットと HYPER-V ネットワーク仮想化 (HNV)](#bkmk_hnv)

- [設定とライブ移行](#bkmk_live)

- [転送されたパケットの MAC アドレスの使用](#bkmk_mac)

- [セット チームを管理します。](#bkmk_manage)

## <a name="set-overview"></a><a name="bkmk_over"></a>セットの概要

SET は、Hyper-v を含む環境で使用できる代替 NIC チーミングソリューションであり、 \( Windows Server 2016 でソフトウェアによって定義されたネットワーク SDN スタックを使用でき \) ます。 セットは、HYPER-V 仮想スイッチにいくつかの NIC チーミング機能を統合します。

セットには、1 つまたは 8 物理イーサネット ネットワーク アダプター間で 1 つまたは複数のソフトウェア ベースの仮想ネットワーク アダプターにグループ化することができます。 これらの仮想ネットワーク アダプターでは、高速なパフォーマンスとネットワーク アダプターに障害が発生した場合のフォールト トレランスを提供します。

チームに配置する同じ物理的な HYPER-V ホスト上で、セットのメンバーのネットワーク アダプターをすべてにインストールする必要があります。

> [!NOTE]
> セットの使用は Windows Server 2016 で HYPER-V 仮想スイッチでのみサポートされます。 Windows Server 2012 R2 のセットを展開することはできません。

チーム化された Nic を同じ物理スイッチまたは異なる物理スイッチに接続できます。 Nic を別々 のスイッチに接続する場合、同じサブネットに両方のスイッチを引き起こすことがあります。

次の図は、一連のアーキテクチャを示しています。

![セット アーキテクチャ](../media/RDMA-and-SET/set_architecture.jpg)

セットは、HYPER-V 仮想スイッチに統合されているので、仮想マシン (VM) の内部セットを使用することはできません。 Vm 内の NIC チーミングを使用すること、ただしします。

詳細については、次を参照してください。 [仮想マシン (Vm) での NIC チーミング](../../networking/technologies/nic-teaming/nic-teaming.md)します。

さらに、一連のアーキテクチャは、チームのインターフェイスを公開しません。 代わりに、HYPER-V 仮想スイッチ ポートを構成する必要があります。

## <a name="set-availability"></a><a name="bkmk_avail"></a>セットの可用性

セットは、Hyper-v ホストと SDN スタックを含む Windows Server 2016 のすべてのバージョンで使用できます。 さらに、ツールがサポートされているクライアントのオペレーティング システムを実行しているリモート コンピューターからセットを管理するのに Windows PowerShell コマンドとリモート デスクトップ接続を使用することができます。

## <a name="supported-nics-for-set"></a><a name="bkmk_nics"></a>セットのサポートされている Nic

Windows \( \) Server 2016 のセットチームで、Windows ハードウェア認定およびロゴの WHQL テストに合格したイーサネット NIC を使用できます。 セットチームのメンバーであるすべてのネットワークアダプターが同一である必要があり \( ます。つまり、同じ製造元、同じモデル、同じファームウェア、およびドライバーである必要があり \) ます。 セットは、チーム内の 1 つまたは 8 のネットワーク アダプター間でサポートします。

## <a name="set-compatibility-with-windows-server-networking-technologies"></a><a name="bkmk_compat"></a>Windows Server ネットワーク テクノロジとの互換性を設定します。

セットは、Windows Server 2016 では、次のネットワーク テクノロジとの互換性です。

- データセンターブリッジング \( DCB\)

- Windows Server 2016 では HYPER-V ネットワーク仮想化 - NV GRE と VxLAN がサポートされます。
- 受信側チェックサムのオフロード \( IPv4、IPv6、TCP \) -これらは、SET チームのメンバーがサポートしている場合にサポートされます。

- リモートダイレクトメモリアクセス \( RDMA\)

- シングルルート i/o 仮想化 \( sr-iov\)

- 送信側のチェックサム \( は、IPv4、IPv6、TCP のオフロード \) に対応しています。これらは、すべての SET チームメンバーがサポートしている場合にサポートされます。

- 仮想マシンキュー \( VMQ\)

- 仮想 Receive Side Scaling \( RSS\)

SET は、Windows Server 2016 の次のネットワークテクノロジと互換性がありません。

- 802.1 x 認証。 802.1 x 拡張認証プロトコル \( EAP \) パケットは、セットのシナリオでは、Hyper-v 仮想スイッチによって自動的に削除され \- ます。

- IPsec タスクオフロード \( ipsecto \) 。 これは、ほとんどのネットワークアダプターではサポートされていないレガシテクノロジであり、存在する場合は既定で無効になっています。

- \( \) ホストまたはネイティブオペレーティングシステムでの QoSpacer.exeの使用。 これらの QoS シナリオは Hyper-v のシナリオではないため、これら \- のテクノロジは交差しません。 また、QoS は使用できますが、既定では有効になっていません。 QoS を意図的に有効にする必要があります。

- 側合体 \( RSC \) を受信します。 RSC は、Hyper-v 仮想スイッチによって自動的に無効にされ \- ます。

- Receive side scaling \( RSS \) 。 Hyper-v では VMQ と VMMQ のキューが使用されるため、仮想スイッチを作成すると RSS は常に無効になります。

- TCP Chimney オフロード。 既定では、このテクノロジは無効になっています。

- 仮想マシン \( の qos VM-qos \) 。 VM QoS は使用できますが、既定では無効になっています。 SET 環境で VM の QoS を構成すると、QoS の設定によって予期しない結果が発生します。

## <a name="set-modes-and-settings"></a><a name="bkmk_modes"></a>セットのモードと設定

NIC チーミングとは異なり、セット チームを作成するときに、チーム名インストールを構成することはできません。 さらに、NIC チーミングでサポートされてスタンバイ アダプターを使用してはセットではサポートされていません。 セットを展開するときに、すべてのネットワーク アダプターがアクティブとスタンバイ モードでは [なし] です。

NIC チーミングとセットのもう 1 つ重要な違いは、NIC チーミングが提供する 3 つの異なるチーミング モードの選択のみセットをサポートしている **スイッチに依存しない** モードです。 独立したスイッチのモードでは、スイッチまたはスイッチの設定のチーム メンバーが接続されているセット チームの存在に対応していないし、チーム メンバーを設定するネットワーク トラフィックを分散する方法を特定できません - セット チームが一連のチーム メンバー間で受信ネットワーク トラフィックを分散する代わりに、します。

新しいセット チームを作成するときに、次のチームのプロパティを構成する必要があります。

- メンバーのアダプター

- 負荷分散モード

### <a name="member-adapters"></a>メンバーのアダプター

セットのチームを作成する場合は、一連のチーム メンバーのアダプターとして、HYPER-V 仮想スイッチにバインドされている最大 8 つの同一のネットワーク アダプターを指定する必要があります。

### <a name="load-balancing-mode"></a>負荷分散モード

オプション セットをチームの負荷分散の分散モードは **HYPER-V ポート** と **動的** します。

**Hyper-v ポート**

Vm は、HYPER-V 仮想スイッチのポートに接続されます。 セット チームの HYPER-V ポートのモードを使用している場合、HYPER-V 仮想スイッチ ポートと関連付けられている MAC アドレスは、チーム メンバーのセット間のネットワーク トラフィックを分割に使用されます。

> [!NOTE]
> パケット ダイレクトでは、チーミング モードと組み合わせてセットを使用すると  **スイッチに依存しない** と負荷分散モード **HYPER-V ポート** が必要です。

隣接するスイッチは、指定したポートで、特定の MAC アドレスを常には、あるため、スイッチは、MAC アドレスのポートに受信負荷 (ホストのスイッチのトラフィック) を配布します。 これは特に便利ですバーチャル マシン キュー (VMQs) を使用している場合、キューは、トラフィックが到着する期待される場所で特定の NIC で配置できるためです。

ただし、ホストにいくつかの Vm がある場合は、このモードはありませんな負荷分散を実現するために必要なレベルです。 このモードは、単一のインターフェイスで利用できる帯域幅を 1 つの VM (つまり、1 つのスイッチ ポートからのトラフィック) を常にも制限されます。

**動的**

この負荷分散モードでは、次の利点を提供します。

- TCP ポートと IP アドレスのハッシュに基づいて、送信の負荷が分散されます。  動的モードもバランスが再調整負荷をリアルタイムに特定の送信フローは、チーム メンバーのセット間で双方向に移動できるようにします。

- HYPER-V ポートのモードと同じ方法では、着信負荷が分散されます。

このモードでの送信の負荷が flowlets の概念に基づいて動的に分散します。 人間の音声認識に単語や文の末尾にある自然な改行がある場合と同様 TCP フロー (TCP 通信ストリーム) が自然に発生した中断もあります。 このような 2 つの区切りの間の TCP フローの一部を flowlet と呼びます。

動的モード アルゴリズムは、十分な長さの中断が TCP フロー - で発生した場合などに flowlet 境界が検出されたことを検出すると、アルゴリズムで該当する場合は、別のチーム メンバーへの流れが自動的に再分散します。  一般的でない状況によっては、アルゴリズム可能性があります、flowlets が含まれていないフローを再調整も定期的にします。 このため、TCP フローとチーム メンバー間のアフィニティは動的な分散アルゴリズムは、チーム メンバーの作業負荷のバランスを取る動作いつでも変更できます。

## <a name="set-and-virtual-machine-queues-vmqs"></a><a name="bkmk_vmq"></a>セットと仮想マシン キュー (VMQs)

VMQ と SET は連携して機能します。 Hyper-v を使用してを設定するときは常に VMQ を有効にする必要があります。

> [!NOTE]
> チーム メンバーには、すべての設定で使用するキューの合計数は常に設定します。 NIC チーミングには、キューの合計モードこの呼び出されます。

ほとんどのネットワークアダプターには、Receive Side Scaling RSS または VMQ のいずれかに使用できるキューがありますが、両方を同時に使用することはでき \( \) ません。

VMQ 設定の一部では、RSS のキューの設定に見えますが、どの機能によって RSS および VMQ の両方の使用は現在使用されている一般的なキューの設定で、実際には。 各 NIC の詳細プロパティには、との値が含ま `*RssBaseProcNumber` `*MaxRssProcessors` れます。

次に、システムパフォーマンスを向上させる VMQ 設定をいくつか示します。

- 各 NIC は2以上の偶数に設定するのが理想的です `*RssBaseProcNumber` 。 これは、最初の物理プロセッサ (コア 0 \( 論理プロセッサ0および 1 \) ) が、通常はシステム処理のほとんどを行い、ネットワーク処理がこの物理プロセッサから切り離されているためです。

>[!NOTE]
>コンピューターのアーキテクチャによっては、物理プロセッサごとに2つの論理プロセッサが搭載されていないため、このようなコンピューターでは、ベースプロセッサは1以上にする必要があります。 確信が持てない場合は、ホストが物理プロセッサアーキテクチャごとに2つの論理プロセッサを使用していると仮定します。

- チームメンバーのプロセッサは、実用的で、重複していない程度にする必要があります。 たとえば、 \( 2 10Gbps nic のチームを持つ4コアホスト8論理プロセッサでは、1つ目は \) 基本プロセッサ2を使用し、4コアを使用するように設定できます。2つ目は基本プロセッサ6を使用し、2つのコアを使用するように設定されます。

## <a name="set-and-hyper-v-network-virtualization-hnv"></a><a name="bkmk_hnv"></a>SET と Hyper-v ネットワーク仮想化 \( hnv\)

セットは、Windows Server 2016 で HYPER-V ネットワーク仮想化の完全な互換性です。 HNV の管理システムでは、HNV トラフィック用に最適化された方法でネットワーク トラフィックの負荷を配布する設定は、セットのドライバーに情報を提供します。

## <a name="set-and-live-migration"></a><a name="bkmk_live"></a>設定とライブ移行

ライブマイグレーションは、Windows Server 2016 でサポートされています。

## <a name="mac-address-use-on-transmitted-packets"></a><a name="bkmk_mac"></a>転送されたパケットの MAC アドレスの使用

動的な負荷分散を使用してセットチームを構成すると、1つの VM などの1つのソースからのパケット \( \) は、同時に複数のチームメンバーに分散されます。

スイッチが混同されないようにし、MAC フラッピングアラームを防止するために、を設定すると、ソースの MAC アドレスが、関連付けられたチームメンバー以外のチームメンバーで送信されるフレームの別の MAC アドレスに置き換えられます。 このため、各チーム メンバーが別の MAC アドレスを使用して、MAC アドレスの競合はしない限り、エラーが発生したためにできませんでした。

プライマリ NIC で障害が検出されると、セットチーミングソフトウェアは、一時的な関連チームメンバーとして機能するように選択されたチームメンバー \( (vm のインターフェイスとしてスイッチに表示される) の vm の MAC アドレスを使用して開始 \) します。

この変更は、MAC アドレスをソースとして VM の MAC アドレスを持つ VM のアフィニティを設定したチーム メンバーに送信するとしたトラフィックのみに適用されます。 その他のトラフィックは、どのようなソースは、障害発生前に使用した MAC アドレスと送信されます。

チームの構成方法に基づいて MAC アドレスの置き換え動作のチーム化のセットを記述する一覧を以下にします。

- HYPER-V ポート分布でスイッチに依存しないモードで

    - 各 vmSwitch ポートが、チーム メンバーに関連付けられます

    - ポートが関連付けられ、そのチーム メンバーにすべてのパケットを送信します。

    - ソース MAC の置換は行われません

- スイッチに依存しないモード動的配布と

    - 各 vmSwitch ポートが、チーム メンバーに関連付けられます

    - ARP/NS のすべてのパケットが、ポートが関連付けられ、そのチーム メンバーに送信されます。

    - アフィニティを設定したチーム メンバーは、チーム メンバーに送信されるパケットがソース MAC アドレスの置き換えが行われますを持っていません

    - アフィニティを設定したチーム メンバー以外のチーム メンバーに送信されるパケットがソース MAC アドレスの置換が完了には

## <a name="managing-a-set-team"></a><a name="bkmk_manage"></a>セット チームを管理します。

System Center Virtual Machine Manager VMM を使用してセットチームを管理することをお勧めし \( \) ますが、Windows PowerShell を使用して設定を管理することもできます。 次のセクションでは、Windows PowerShell コマンド セットの管理に使用できるを提供します。

VMM を使用してセットチームを作成する方法の詳細については、「System Center VMM ライブラリ」トピックの「 [論理スイッチの](/system-center/vmm/network-switch)セットアップ」セクションを参照してください。

### <a name="create-a-set-team"></a>セットチームを作成する

**新しい-VMSwitch** Windows PowerShell コマンドを使用して、Hyper-v 仮想スイッチを作成するときに、セットチームを作成する必要があります。

Hyper-v 仮想スイッチを作成する場合は、コマンド構文に新しい **EnableEmbeddedTeaming** パラメーターを含める必要があります。 次の例では、埋め込みチーミングと2つの初期チームメンバーを含む  **Teamedvswitch** という名前の hyper-v スイッチが作成されています。

```
New-VMSwitch -Name TeamedvSwitch -NetAdapterName "NIC 1","NIC 2" -EnableEmbeddedTeaming $true
```

**EnableEmbeddedTeaming** パラメーターは、 **NetAdapterName** の引数が1つの Nic ではなく nic の配列である場合に、Windows PowerShell によって想定されます。 その結果、次のように前のコマンドを変更する可能性があります。

```
New-VMSwitch -Name TeamedvSwitch -NetAdapterName "NIC 1","NIC 2"
```

作成する場合は、セットに対応したスイッチと 1 つのチーム メンバーは後で、チーム メンバーを追加できるように EnableEmbeddedTeaming パラメーターを使用する必要があります。

```
New-VMSwitch -Name TeamedvSwitch -NetAdapterName "NIC 1" -EnableEmbeddedTeaming $true
```

### <a name="adding-or-removing-a-set-team-member"></a>追加または SET チーム メンバーを削除します。

**VMSwitchTeam** コマンドには、 **NetAdapterName** オプションが含まれています。 セットチーム内のチームメンバーを変更するには、 **NetAdapterName** オプションの後にチームメンバーの必要な一覧を入力します。 **Teamedvswitch** が最初に nic 1 と nic 2 で作成された場合、次のコマンド例では、set チームメンバー "nic 2" を削除し、新しいセットチームメンバー "nic 3" を追加します。

```
Set-VMSwitchTeam -Name TeamedvSwitch -NetAdapterName "NIC 1","NIC 3"
```

### <a name="removing-a-set-team"></a>セットのチームを削除します。

セットチームを削除できるのは、セットチームを含む Hyper-v 仮想スイッチを削除することだけです。  Hyper-v 仮想スイッチを削除する方法については、「 [remove-VMSwitch](/powershell/module/hyper-v/remove-vmswitch) 」を参照してください。 次の例では、 **Setvswitch** という名前の仮想スイッチを削除します。

```
Remove-VMSwitch "SETvSwitch"
```

### <a name="changing-the-load-distribution-algorithm-for-a-set-team"></a>セット チームの負荷分散アルゴリズムを変更します。

**VMSwitchTeam** コマンドレットには、 **LoadBalancingAlgorithm** オプションがあります。 このオプションは、 **Hypervport** または **Dynamic** の2つの値のいずれかを使用します。 を設定またはスイッチに組み込まれたチームの負荷分散アルゴリズムを変更するには、このオプションを使用します。

次の例では、 **Teamedvswitch** という名前の VMSwitchTeam は、 **動的** 負荷分散アルゴリズムを使用しています。
```
Set-VMSwitchTeam -Name TeamedvSwitch -LoadBalancingAlgorithm Dynamic
```
### <a name="affinitizing-virtual-interfaces-to-physical-team-members"></a>物理チームメンバーへの仮想インターフェイスの関連付け

セットを使用すると、仮想インターフェイス \( (Hyper-v 仮想スイッチポート \) と、チーム内の物理 nic の1つ) の間にアフィニティを作成できます。

たとえば、SMB ダイレクト用に2つのホスト vNICs を作成する場合、 \- 「 [SET と RDMA vnics を使用して Hyper-v 仮想スイッチを作成](#bkmk_set-rdma)する」のセクションで、2つの vnics が異なるチームメンバーを使用するようにすることができます。

このセクションのスクリプトにを追加すると、次の Windows PowerShell コマンドを使用できます。

```powershell
Set-VMNetworkAdapterTeamMapping -VMNetworkAdapterName SMB_1 –ManagementOS –PhysicalNetAdapterName “SLOT 2”
Set-VMNetworkAdapterTeamMapping -VMNetworkAdapterName SMB_2 –ManagementOS –PhysicalNetAdapterName “SLOT 3”
```

このトピックの詳細については、「 [Windows Server 2016 NIC And Switch Embedded チーミングユーザーガイド](https://gallery.technet.microsoft.com/Windows-Server-2016-839cb607?redir=0)」の「4.2.5」セクションを参照してください。
