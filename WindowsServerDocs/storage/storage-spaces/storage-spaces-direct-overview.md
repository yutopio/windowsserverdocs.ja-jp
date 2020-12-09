---
title: 記憶域スペース ダイレクトの概要
ms.author: cosdar
manager: dongill
ms.topic: article
author: cosmosdarwin
ms.date: 07/24/2020
ms.assetid: 8bd0d09a-0421-40a4-b752-40ecb5350ffd
description: 内部記憶域を持つサーバーをソフトウェアによって定義された記憶域ソリューションにクラスター化できるようにする、Windows Server および Azure Stack HCI の機能である記憶域スペースダイレクトの概要を説明します。
ms.localizationpriority: medium
ms.openlocfilehash: 726bb42c2f652bf6cd6165adb0afed0237040aaf
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96864871"
---
# <a name="storage-spaces-direct-overview"></a>記憶域スペース ダイレクトの概要

>適用対象: Azure Stack HCI、Windows Server 2019、Windows Server 2016

記憶域スペース ダイレクトは、業界標準のサーバーとローカルで接続されているドライブを使用して、従来の SAN や NAS 配列の何分の 1 かのコストで、可用性と拡張性が高いソフトウェア定義の記憶域を作ります。 収束または集約型アーキテクチャは、調達とデプロイを大幅に簡素化します。一方、キャッシュ、記憶域階層、消去コーディングなどの機能は、RDMA ネットワークや NVMe ドライブなどの最新のハードウェアイノベーションと共に、優れたの効率とパフォーマンスを実現します。

記憶域スペースダイレクトは、 [AZURE STACK HCI](/azure-stack/hci/)、windows Server 2019 Datacenter、windows Server 2016 datacenter、および [Windows Server Insider Preview ビルド](https://insider.windows.com/for-business-getting-started-server/)に含まれています。

共有 SAS クラスターやスタンドアロンサーバーなど、記憶域スペースの他のアプリケーションについては、「 [記憶域スペースの概要](overview.md)」を参照してください。 Windows 10 PC で記憶域スペースを使用する方法の詳細については、「 [windows 10 での記憶域スペース](https://support.microsoft.com/help/12438/windows-10-storage-spaces)」を参照してください。

| 説明 | ドキュメント |
|--|--|
| **概要**<br><ul><li>概要 (このページ)</li><li>[キャッシュについて](understand-the-cache.md)</li><li>[フォールト トレランスと記憶域の効率](storage-spaces-fault-tolerance.md)<li>[ドライブの対称性に関する考慮事項](drive-symmetry-considerations.md)</li><li>[記憶域の再同期を理解して管理する](understand-storage-resync.md)</li><li>[クラスターとプール クォーラムの概要](understand-quorum.md)</li><li>[クラスター セット](cluster-sets.md)</li> | **プラン**<br><ul><li>[ハードウェア要件](storage-spaces-direct-hardware-requirements.md)</li><li>[CSV のメモリ内読み取りキャッシュを使用する](csv-cache.md)</li><li>[ドライブの選択](choosing-drives.md)</li><li>[ボリュームの計画](plan-volumes.md)</li><li>[ゲスト VM クラスターの使用](storage-spaces-direct-in-vm.md)</li><li>[ディザスター リカバリー](storage-spaces-direct-disaster-recovery.md)</li> |
| **デプロイする**<br><ul><li>[記憶域スペース ダイレクトの展開](deploy-storage-spaces-direct.md)</li><li>[ボリュームの作成](create-volumes.md)</li><li>[入れ子の回復性](nested-resiliency.md)</li><li>[クォーラムの構成](../../failover-clustering/manage-cluster-quorum.md)</li><li>[記憶域スペース ダイレクト クラスターを Windows Server 2019 にアップグレードする](upgrade-storage-spaces-direct-to-windows-server-2019.md)</li><li>[永続的なメモリの理解とデプロイ](deploy-pmem.md)</li> | **管理**<br><ul><li>[Windows Admin Center による管理](../../manage/windows-admin-center/use/manage-hyper-converged.md)</li><li>[サーバーまたはドライブの追加](add-nodes.md)</li><li>[メンテナンスのためサーバーをオフラインにする](maintain-servers.md)</li><li>[サーバーの削除](remove-servers.md)</li><li>[ボリュームの拡張](resize-volumes.md)</li><li>[ボリュームの削除](delete-volumes.md)</li><li>[ドライブ ファームウェアの更新](../update-firmware.md)</li><li>[パフォーマンス履歴](performance-history.md)</li><li>[ボリュームの割り当てを区切る](delimit-volume-allocation.md)</li><li>[ハイパー収束クラスターでの Azure Monitor の使用](configure-azure-monitor.md)</li> |
| **トラブルシューティング**<br><ul><li>[トラブルシューティング シナリオ](troubleshooting-storage-spaces.md)</li><li>[正常性状態と操作状態のトラブルシューティングを行う](storage-spaces-states.md)</li><li>[記憶域スペースダイレクトを使用した診断データの収集](data-collection.md)</li><li>[記憶域クラスのメモリの状態の管理](Storage-class-memory-health.md)</li> | **最近のブログ投稿**<br><ul><li>[1370万記憶域スペースダイレクトの IOPS: ハイパー集約型インフラストラクチャの新しい業界レコード](https://techcommunity.microsoft.com/t5/storage-at-microsoft/the-new-hci-industry-record-13-7-million-iops-with-windows/ba-p/428314)</li><li>[Windows Server 2019 のハイパー集約インフラストラクチャ-カウントダウンクロックが開始されました。](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)</li><li>[Windows Server サミットによる5つの大きなお知らせ](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)</li><li>[1万記憶域スペースダイレクトクラスターおよびカウントしています...](https://techcommunity.microsoft.com/t5/storage-at-microsoft/storage-spaces-direct-10-000-clusters-and-counting/ba-p/428185)</li></ul> |

## <a name="videos"></a>ビデオ

**クイックビデオの概要 (5 分)**

> [!Video https://www.youtube-nocookie.com/embed/raeUiNtMk0E]

**Microsoft Ignite 2018 (1 時間) の記憶域スペースダイレクト**

> [!Video https://www.youtube-nocookie.com/embed/5kaUiW3qo30]

**Microsoft Ignite 2017 (1 時間) の記憶域スペースダイレクト**

> [!Video https://www.youtube-nocookie.com/embed/YDr2sqNB-3c]

**Microsoft Ignite 2016 でイベントを開始する (1 時間)**

> [!Video https://www.youtube-nocookie.com/embed/LK2ViRGbWs]

## <a name="key-benefits"></a>主な利点

| Image | 説明 |
|--|--|
| ![シンプルさ](media/storage-spaces-direct-in-windows-server-2016/simplicity-icon.png) | **簡便性.** Windows Server 2016 を実行する業界標準のサーバーから、最初の記憶域スペース ダイレクト クラスターに移行するまでにかかる時間は 15 分未満です。 System Center ユーザーの場合、1 個のチェックボックスのみで展開が完了します。 |
| ![優れたのパフォーマンス](media/storage-spaces-direct-in-windows-server-2016/performance-icon.png) | **優れたパフォーマンス。** 記憶域スペース ダイレクトは、すべてフラッシュでもハイブリッドでも、一貫性があり、低遅延で、[サーバーあたりの混合 4K ランダム IOPS が 150,000 回](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)を軽々と超えます。これは、ハイパーバイザーが組み込まれているアーキテクチャ、その組み込みの読み取り/書き込みキャッシュ、PCIe バスに直接マウントされた最新の NVMe ドライブのサポートの利点です。 |
| ![フォールト トレランス](media/storage-spaces-direct-in-windows-server-2016/fault-tolerance-icon.png) | **フォールトトレランス。** 組み込みの回復機能によって、可用性を維持したまま、ドライブ、サーバー、またはコンポーネントのエラーが処理されます。 [シャーシおよびラックのフォールト トレランス](../../failover-clustering/fault-domains.md)向けに大規模な展開も構成できます。 ハードウェアで障害が発生した場合は、交換するだけで済みます。ソフトウェアは自己修復されるので、複雑な管理手順は必要ありません。 |
| ![リソースの効率](media/storage-spaces-direct-in-windows-server-2016/efficiency-icon.png) | **リソースの効率。** イレイジャー コーディングは、ローカル再構築コードや ReFS リアルタイム階層などの独自の新技術で記憶域の効率を最大 2.4x に向上し、そのメリットをハード ディスク ドライブや混合ホット/コールド ワークロードにまで広げています。さらに、CPU 使用量が最小限に抑えられるので、最もリソースが必要な場所、つまり VM にリソースを戻すことができます。 |
| ![管理の容易性](media/storage-spaces-direct-in-windows-server-2016/manageability-icon.png) | **管理のしやすさ**。 [記憶域 QoS 制御](../storage-qos/storage-qos-overview.md)で、VM ごとの IOPS の下限値と上限値を使用して、負荷が高い VM を監視します。 [ヘルス サービス](../../failover-clustering/health-service-overview.md)は継続的な組み込みの監視機能とアラート機能を提供します。また、新しい API を使用して、高機能でクラスター全体のパフォーマンスおよび容量メトリックを簡単に収集できます。 |
| ![スケーラビリティ](media/storage-spaces-direct-in-windows-server-2016/scalability-icon.png) | **スケーラビリティ**。 最大 16 台のサーバー、400 台を超えるドライブで、クラスターあたり最大 1 ペタバイト (1,000 テラバイト) の記憶域を実現できます。 スケール アウトするには、単にドライブを追加するか、サーバーを追加します。記憶域スペース ダイレクトによって新しいドライブが自動的に追加され、使用されるようになります。 記憶域の効率とパフォーマンスは、規模に応じた予測どおりに改善されます。 |

## <a name="deployment-options"></a>デプロイ オプション

記憶域スペース ダイレクトは、2 つの異なる展開オプション向けに設定されました。

### <a name="converged"></a>収束済み

**記憶域とコンピューティングは別のクラスターにあります。** コンバージド展開オプションは、"非集約型" とも呼ばれ、記憶域スペース ダイレクト上にスケールアウト ファイル サーバー (SoFS) を重ねることで、SMB 3 ファイル共有上のネットワーク接続記憶域を提供します。 これにより、記憶域クラスターとは独立して計算/ワークロードをスケーリングできるので、サービス プロバイダーや大企業向けの Hyper-V IaaS (サービスとしてのインフラストラクチャ) など、大規模な展開には不可欠です。

![記憶域スペース ダイレクトは、スケール アウト ファイル サーバー機能を使用するストレージを別のサーバーまたはクラスター内の Hyper-V VM に提供します。](media/storage-spaces-direct-in-windows-server-2016/converged-minimal.png)

### <a name="hyper-converged"></a>ハイパーコンバージド

**コンピューティングおよびストレージ用の 1 つのクラスター。** ハイパーコンバージド展開オプションでは、ローカル ボリュームに記憶域があり、ファイルを格納するサーバー上で、Hyper-V 仮想マシンまたは SQL Server データベースを直接実行します。 この展開では、ファイル サーバーのアクセス権やアクセス許可を構成する必要がないので、中小規模の企業や、リモート オフィスや支社の展開の場合にはハードウェアのコストを削減できます。 「 [Deploy 記憶域スペースダイレクト](deploy-storage-spaces-direct.md)」を参照してください。

![記憶域スペース ダイレクトが、同じクラスター内の Hyper-V VM にストレージを提供](media/storage-spaces-direct-in-windows-server-2016/hyper-converged-minimal.png)

## <a name="how-it-works"></a>しくみ

記憶域スペース ダイレクトは、Windows Server 2012 で初めて導入された記憶域スペースが進化したものです。 記憶域スペース ダイレクトは現在の Windows Server でなじみのある多くの機能を利用しています。たとえば、フェールオーバー クラスタリング、クラスター共有ボリューム (CSV) ファイル システム、サーバー メッセージ ブロック (SMB) 3、そして当然ながら記憶域スペースです。 また、ソフトウェア記憶域バスを代表として、新しいテクノロジも導入しています。

ここでは、記憶域スペース ダイレクトのスタックの概要について説明します。

![記憶域スペース ダイレクトのスタック](media/storage-spaces-direct-in-windows-server-2016/converged-full-stack.png)

**ネットワーキング ハードウェア。** 記憶域スペース ダイレクトは、イーサネット上のサーバー間の通信に SMB ダイレクトや SMB マルチチャネルを含む SMB3 を使用しています。 リモートダイレクト メモリ アクセス (RDMA) に対応する 10+ GbE を強くお勧めします (iWARP または RoCE)。

**記憶域ハードウェア。** SATA、SAS、または NVMe ドライブがローカル接続された 2 台から 16 台のサーバー。 各サーバーには 2 台以上のソリッドステート ドライブ、4 台以上の追加ドライブが必要です。 SATA デバイスと SAS デバイスは、ホストバス アダプター (HBA) と SAS エキスパンダーの背後に配置することをお勧めします。 マイクロソフトのパートナー製のプラットフォーム (近日公開予定) は、慎重に設計され、広範囲にわたって検証されているので、強くお勧めします。

**フェールオーバークラスタリング。** サーバーの接続には、Windows Server に組み込まれているクラスタリング機能が使用されます。

**ソフトウェアの記憶域バス。** ソフトウェア記憶域バスは、記憶域スペース ダイレクトで導入された新機能です。 ソフトウェア記憶域バスはクラスター全体にまたがり、ソフトウェア定義の記憶域ファブリックを確立するので、すべてのサーバーが相互のローカル ドライブすべてを見ることができます。 コストがかかり、制限が多いファイバー チャネルや共有 SAS ケーブル接続の代替として考えることができます。

**記憶域バス層キャッシュ。** ソフトウェア記憶域バスは、現在最速のドライブ (SSD など) を低速なドライブ (HDD など) に動的にバインドすることで、IO 速度とスループットを向上するサーバー側の読み取り/書き込みキャッシュを提供します。

**記憶域プール。** 記憶域スペースの基礎となるドライブのコレクションは、記憶域プールと呼ばれます。 記憶域プールは自動的に作成され、対象となるすべてのドライブは自動的に検出され、記憶域プールに追加されます。 既定の設定で、1 クラスターに 1 つのプールを使用することを強くお勧めします。 詳しくは、[記憶域プールの詳細に関するブログの記事](https://techcommunity.microsoft.com/t5/storage-at-microsoft/deep-dive-the-storage-pool-in-storage-spaces-direct/ba-p/425959)を参照してください。

**記憶域スペース。** 記憶域スペースは [、ミラーリング、消去コーディング、またはその両方](storage-spaces-fault-tolerance.md)を使用して、仮想ディスクへのフォールトトレランスを提供します。 記憶域スペースは、プール内のドライブを使用する分散型でソフトウェア定義の RAID と考えることができます。 記憶域スペース ダイレクトでは、このような仮想ディスクは、ドライブまたはサーバー エラーが同時に 2 つ発生した場合でも回復できますが (別のサーバーに各データ コピーを持つ 3 方向ミラーリングなど)、シャーシとラックのフォールト トレランスも実装できます。

**弾力性ファイルシステム (ReFS)。** ReFS は、仮想化に特化して構築された高度なファイルシステムです。 作成、拡張、チェックポイントのマージなどの .vhdx ファイル操作の大幅な高速化、ビット エラーを検出して修正する組み込みのチェックサムなどの機能もあります。 また、使用量に基づき、リアルタイムで、いわゆる "ホット" 記憶域階層と "コールド" 記憶域階層間でデータを回転させる、リアルタイム階層化も導入されています。

**クラスターの共有ボリューム。** CSV ファイル システムは、すべての ReFS ボリュームを任意のサーバーからアクセスできる 1 つの名前空間に統合します。そのため、各サーバーに対して、すべてのボリュームはローカルにマウントされているかのように見え、動作します。

**スケールアウト ファイル サーバー。** この最後の層は、コンバージド展開の場合にのみ必要です。 Hyper-V を実行する別のクラスターなど、クライアントに対して、ネットワーク上で SMB3 アクセス プロトコルを使用したリモート ファイル アクセスを提供します。実質的に、記憶域スペース ダイレクトをネットワーク接続記憶域 (NAS) に変える機能があります。

## <a name="customer-stories"></a>顧客事例

記憶域スペースダイレクトを実行している世界中の [1万クラスター](https://techcommunity.microsoft.com/t5/storage-at-microsoft/storage-spaces-direct-10-000-clusters-and-counting/ba-p/428185) があります。 2つのノードのみを展開する小規模企業から、大規模な企業や数百のノードを展開している組織のすべての規模の組織は、重要なアプリケーションやインフラストラクチャの記憶域スペースダイレクトに依存しています。

[Microsoft.com/HCI](https://www.microsoft.com/hci)にアクセスして、ストーリーを読み取ります。

[![顧客のロゴのグリッド](media/storage-spaces-direct-in-windows-server-2016/customer-stories.png)](https://www.microsoft.com/hci)

## <a name="management-tools"></a>管理ツール

記憶域スペースダイレクトの管理や監視には、次のツールを使用できます。

| 名前 | グラフィックまたはコマンドライン | 有料または同梱されていますか? |
|-----------------|----------------------------|-------------------|
| [Windows Admin Center](../../manage/windows-admin-center/overview.md)     | グラフィカル    | 含まれる |
| サーバーマネージャー & フェールオーバークラスターマネージャー                                 | グラフィカル    | 含まれる |
| Windows PowerShell                                                        | コマンド ライン | 含まれる |
| [System Center Virtual Machine Manager (SCVMM)](/system-center/vmm/s2d) <br>& [Operations Manager (SCOM)](https://www.microsoft.com/download/details.aspx?id=54700) | グラフィカル    | 有料     |

## <a name="get-started"></a>はじめに

[Microsoft Azure で](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)記憶域スペース ダイレクトを試すか、「[Windows Server 評価版ソフトウェア](https://go.microsoft.com/fwlink/?linkid=842602)」から 180 日間ライセンスが有効な Windows Server の評価版をダウンロードします。

## <a name="additional-references"></a>その他の参照情報

- [フォールト トレランスと記憶域の効率](storage-spaces-fault-tolerance.md)
- [記憶域レプリカ](../storage-replica/storage-replica-overview.md)
- [Microsoft ブログの Storage](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)
- [Storage Spaces Direct throughput with iWARP (iWARP を使った記憶域スペース ダイレクトのスループット)](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB) (TechNet ブログ)
- [Windows Server のフェールオーバー クラスタリングの新機能に関する記事](../../failover-clustering/whats-new-in-failover-clustering.md)
- [記憶域のサービスの品質 (QoS)](../storage-qos/storage-qos-overview.md)
- [Windows IT 担当者向けサポート](https://www.microsoft.com/itpro/windows/support)
