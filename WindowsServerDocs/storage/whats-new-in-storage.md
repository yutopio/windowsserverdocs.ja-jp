---
ms.assetid: 0f2a7f7b-aca8-4e5d-ad67-4258e88bc52f
title: Windows Server での記憶域の新機能
description: '詳細情報: Windows Server での記憶域の新機能'
ms.author: jgerend
manager: dongill
ms.topic: article
author: jasongerend
ms.date: 05/29/2019
ms.openlocfilehash: b025960aabe03ed752ecd9ebeb0870166b25826b
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97048590"
---
# <a name="whats-new-in-storage-in-windows-server"></a>Windows Server での記憶域の新機能

>適用先:Windows Server 2019、Windows Server 2016、Windows Server (半期チャネル)

このトピックでは、Windows Server 2019、Windows Server 2016、および Windows Server Semi-Annual Channel リリースでの記憶域の新機能と変更された機能について説明します。

## <a name="whats-new-in-storage-in-windows-server-version-1903"></a>Windows Server での記憶域の新機能、バージョン1903

このリリースの Windows Server では、次の変更とテクノロジが追加されています。

### <a name="storage-migration-service-now-migrates-local-accounts-clusters-and-linux-servers"></a>ストレージ移行サービスでローカル アカウント、クラスターおよび Linux サーバーの移行が可能

ストレージ移行サービスでは、Windows Server の新しいバージョンにサーバーを簡単に移行できます。 これには、アプリやユーザーが何も変更を行わずに、サーバー上のデータのインベントリを作成し、そのデータと構成が新しいサーバーに転送されるグラフィカル ツールがあります。

移行の調整にこのバージョンの Windows Server を使用するときのために、次の機能が追加されています。

- 新しいサーバーへのローカル ユーザーとローカル グループの移行
- フェールオーバー クラスターからの記憶域の移行
- Samba を使用する Linux サーバーからの記憶域の移行
- Azure File Sync を使用した Azure へ移行された共有のより簡単な同期
- Azure などの新しいネットワークへの移行

記憶域移行サービスの詳細については、「[ストレージ移行サービスの概要](storage-migration-service/overview.md)」を参照してください。

### <a name="system-insights-disk-anomaly-detection"></a>システム インサイトでのディスク異常の検出

[システム インサイト](../manage/system-insights/overview.md)は、ローカルで Windows Server のシステム データを分析し、サーバーの機能の分析情報を提供する予測分析機能です。 これには多数の機能が組み込まれていますが、ディスク異常の検出を初めとする追加機能を Windows Admin Center を使用してインストールできるようになりました。

ディスク異常の検出は、ディスクが通常とは *異なる* 動作をしたとき、それを浮き彫りにする新機能です。 異なるということが必ずしも悪いということではありませんが、これらの異常な瞬間を確認することによって、お使いのシステムの問題の解決に役立つことがあります。

この機能は、Windows Server 2019 を実行するサーバーでも利用できます。

### <a name="windows-admin-center-enhancements"></a>Windows Admin Center の機能強化

Windows Admin Center の新しいリリースがリリースされ、Windows Server に新機能が追加されました。 最新の機能の詳細については、[Windows Admin Center](../manage/windows-admin-center/overview.md)に関するページを参照してください。

## <a name="whats-new-in-storage-in-windows-server-2019-and-windows-server-version-1809"></a>Windows Server 2019 および Windows Server の記憶域の新機能、バージョン1809

このリリースの Windows Server では、次の変更とテクノロジが追加されています。

### <a name="manage-storage-with-windows-admin-center"></a>Windows 管理センターを使用して記憶域を管理する

[Windows 管理センター](../manage/windows-admin-center/overview.md) は、新しいローカルに展開されたブラウザーベースのアプリで、サーバー、クラスター、記憶域スペースダイレクトを使用したハイパー集約型インフラストラクチャ、および Windows 10 pc を管理します。 Windows 以外の追加コストはなく、運用環境で使用する準備ができています。

Windows 管理センターは、windows Server 2019 およびその他のバージョンの Windows で実行されている別のダウンロードですが、それを見逃してしまいたいと思います。

### <a name="storage-migration-service"></a>ストレージ移行サービス

ストレージ移行サービスは、Windows Server の新しいバージョンにサーバーを移行しやすくする新しいテクノロジです。 このサービスには、データをサーバーにインベントリし、データと構成を新しいサーバーに転送して、必要に応じて古いサーバーの ID を新しいサーバーに移行するツールが用意されているため、アプリとユーザーは何も変更する必要がありません。 詳細については、「[ストレージ移行サービス](storage-migration-service/overview.md)」を参照してください。

### <a name="storage-spaces-direct-windows-server-2019-only"></a><a id="storage-spaces-direct"></a>記憶域スペースダイレクト (Windows Server 2019 のみ)

Windows Server 2019 で記憶域スペースダイレクトにはいくつかの機能強化が施されています (記憶域スペースダイレクト Windows Server、Semi-Annual Channel には含まれていません)。

- **ReFS ボリュームの重複除去と圧縮**

    同じボリューム上に、ReFS ファイルシステムの重複除去と圧縮を使用して最大10倍のデータを格納します。 ( [1 回クリックするだけ](https://www.youtube.com/watch?v=PRibTacyKko&feature=youtu.be) で、Windows 管理センターで有効にすることができます)。オプションの圧縮を使用した可変サイズのチャンクストアでは、節約率が最大になりますが、マルチスレッドの後処理アーキテクチャではパフォーマンスに影響を最小限に抑えることができます。 は、最大 64 TB のボリュームをサポートし、各ファイルの最初の 4 TB を重複除去します。

- **永続メモリのネイティブ サポート**

    Intel® Optane™ DC PM や NVDIMM-N を含む永続メモリ モジュールに対するネイティブな記憶域スペース ダイレクト サポートで、類を見ないパフォーマンスが引き出されます。 永続メモリは、アクティブなワーキング セットを加速するためのキャッシュとして使用することも、ミリ秒レベルの低待機時間を保証する容量として使用することもできます。 永続メモリは、他のドライブと同様に PowerShell または Windows Admin Center で管理します。

- **エッジの 2 ノード ハイパーコンバージド インフラストラクチャに対する入れ子の回復性**

    RAID 5+1 から着想を得たまったく新しいソフトウェア回復性オプションで、2 つのハードウェア障害を一度に回避します。 2 ノードの記憶域スペース ダイレクト クラスターで入れ子の回復性を利用すると、一方のサーバー ノードがダウンして他方のサーバー ノードのドライブに障害が発生した場合でも、継続的にアクセス可能な記憶域をアプリと仮想マシンに提供できます。

- **監視として USB フラッシュ ドライブを使用した 2 つのサーバー クラスター**

    ルーターに接続された低コストの USB フラッシュドライブを使用して、2台のサーバーから成るクラスターでミラーリング監視サーバーとして機能します。 サーバーがダウンしてバックアップされると、USB ドライブクラスターは最新のデータがあるサーバーを認識します。 詳細については、 [Microsoft ブログ](https://techcommunity.microsoft.com/t5/storage-at-microsoft/here-s-what-you-missed-8211-five-big-announcements-for-storage/ba-p/428257) の「Storage」と、 [ファイル共有監視を展開する方法に関するドキュメント](../failover-clustering/file-share-witness.md#creating-a-file-share-witness-on-a-router-with-a-usb-device)を参照してください。

- **Windows Admin Center**

    Windows Admin Center の[目的に特化した新しいダッシュボード](../manage/windows-admin-center/use/manage-hyper-converged.md)とエクスペリエンスで、記憶域スペース ダイレクトを管理および監視できます。 ボリュームを作成する、開く、展開する、削除するといった操作をわずか数クリックで実行できます。 クラスター全体から個々の SSD や HDD まで、IOPS や IO 待機時間などのパフォーマンスを監視できます。 Windows Server 2016 および Windows Server 2019 ではコストを追加することなく使用できます。

- **パフォーマンス履歴**

    [組み込みの履歴情報](storage-spaces/performance-history.md)を使用すると、リソース使用率とパフォーマンスを簡単に可視化できます。 コンピューティング、メモリ、ネットワーク、記憶域のカテゴリにわたる 50 以上の重要なカウンターが自動的に収集され、クラスターに最大 1 年間保存されます。 何よりも、インストール、構成、または開始するものはありません。これは動作するだけです。 Windows Admin Center で可視化することも、照会や処理を PowerShell で行うこともできます。

- **クラスターごとに 4 PB まで拡張可能**

    メディア、バックアップ、およびアーカイブのユース ケースに最適なマルチペタバイトの拡張性を実現します。 Windows Server 2019 の記憶域スペース ダイレクトでは、記憶域プールあたり最大 4 ペタバイト (PB) = 4,000 テラバイトの未加工容量がサポートされます。 関連する容量ガイドラインも引き上げられています。たとえば、作成できるボリューム数が 2 倍になり (32 から 64 に増加)、それぞれの大きさも従来の 2 倍になっています (32 TB から 64 TB に増加)。 複数のクラスターをまとめて1つの記憶域名前空間内でさらに大きなスケールを行う [クラスターセット](storage-spaces/cluster-sets.md) にします。 詳細については、 [Microsoft ブログ](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)の「Storage」を参照してください。

- **ミラーリングによって高速化されたパリティで 2 倍の速度を実現**

    ミラーリングによって高速化されたパリティを使用すると、記憶域スペース ダイレクトのボリュームを作成できます。このボリュームでは、RAID-1 と RAID-5/6 の良い部分を組み合わせるような形で、一部がミラー、一部がパリティになっています  (Windows 管理センターで考えている [よりも簡単](https://www.youtube.com/watch?v=R72QHudqWpE) です)。Windows Server 2019 では、最適化により、ミラーアクセラレータのパリティのパフォーマンスが Windows Server 2016 に比べて2倍になっています。

- **ドライブの待機時間に関する外れ値の検出**

    継続的な監視と組み込みの外れ値検出を使用して、異常な待機時間のあるドライブを簡単に識別できます。これは Microsoft Azure の長期的で成功したアプローチによるものです。 平均待機時間や、99パーセンタイルの待機時間など、より微妙なものがあるかどうかにかかわらず、低速のドライブには、PowerShell と Windows 管理センターで "異常待機時間" の状態が自動的にラベル付けされます。

- **フォールト トレランスを向上するボリュームの割り当てを手動で区切る**

    これにより、管理者は記憶域スペースダイレクトでボリュームの割り当てを手動で区切ることができます。 これにより、特定の条件下でフォールトトレランスを大幅に向上させることができますが、管理上の考慮事項と複雑さが増加します。 詳細については、「 [ボリュームの割り当てを区切る](storage-spaces/delimit-volume-allocation.md)」を参照してください。

### <a name="storage-replica"></a><a name="storage-replica2019"></a>記憶域レプリカ

このリリースでは、 [記憶域レプリカ](storage-replica/storage-replica-overview.md) にいくつかの機能強化が行われています。

#### <a name="storage-replica-in-windows-server-standard-edition"></a>Windows Server Standard Edition の記憶域レプリカ

Datacenter Edition に加えて、Windows Server Standard Edition でも記憶域レプリカを使用できるようになりました。 Windows Server Standard Edition で実行されている記憶域レプリカには、次の制限があります。

- 記憶域レプリカは、無制限の数のボリュームではなく、1つのボリュームをレプリケートします。
- ボリュームのサイズは、無制限のサイズではなく、最大 2 TB です。

#### <a name="storage-replica-log-performance-improvements"></a>記憶域レプリカのログのパフォーマンスの向上

また、ストレージレプリカログがレプリケーションを追跡し、レプリケーションのスループットと待機時間を向上させる方法も改善されました。特に、すべてのフラッシュストレージに加えて、相互にレプリケートするクラスターを記憶域スペースダイレクトします。

パフォーマンスの向上を実現するには、レプリケーショングループのすべてのメンバーが Windows Server 2019 を実行している必要があります。

#### <a name="test-failover"></a>[テスト フェールオーバー]

テストまたはバックアップの目的で、レプリケートされたストレージのスナップショットを移行先サーバーに一時的にマウントできるようになりました。 詳細については、「[記憶域レプリカについてよく寄せられる質問](./storage-replica/storage-replica-frequently-asked-questions.md)」をご覧ください。

#### <a name="windows-admin-center-support"></a>Windows Admin Center サポート

Windows 管理センターでは、サーバーマネージャーツールを使用して、レプリケーションのグラフィカル管理をサポートできるようになりました。 これには、サーバー間のレプリケーション、クラスター間のレプリケーション、およびストレッチクラスターレプリケーションが含まれます。

#### <a name="miscellaneous-improvements"></a>その他の機能強化

記憶域レプリカには、次の機能強化も含まれています。

-   自動フェールオーバーが発生するように、非同期ストレッチクラスターの動作を変更します。
-   複数のバグ修正

### <a name="smb"></a>SMB

- **Smb1 およびゲスト認証の削除**: 既定では、Windows Server では、smb1 クライアントとサーバーがインストールされなくなりました。 さらに、SMB2 以降のゲストとして認証する機能は、既定で無効になっています。 詳細については、[Windows 10 バージョン 1709 および Windows Server 1709 のバージョンで、SMBv1 が 既定でインストールされない問題に関するページ](https://support.microsoft.com/help/4034314/smbv1-is-not-installed-by-default-in-windows-10-rs3-and-windows-server)をご覧ください。

- **SMB2/SMB3 のセキュリティと互換性**: レガシ アプリケーションについて SMB2+ の oplock を無効にする機能や、クライアントからの接続ごとに署名や暗号化を要求する機能など、セキュリティやアプリケーションの互換性のための新しいオプションが追加されました。 詳細については、SMBShare PowerShell モジュールのヘルプを確認してください。

### <a name="data-deduplication"></a>データ重複除去

- **データ重複除去で ReFS をサポート**: ReFS による最新ファイル システムの長所とデータ重複除去のいずれかを選択する必要がなくなりました。ReFS を有効にしているときにいつでもデータ重複除去を有効にできるようになりました。 ReFS によって記憶域の効率が 95% 以上向上します。
- **重複除去されたボリュームへの最適化された送受信のための DataPort API**: 開発者は、データ重複除去によって効率的にデータを保存する方法に関する知識を活用して、ボリューム、サーバー、クラスター間で効率的にデータを移動することができます。

### <a name="file-server-resource-manager"></a>File Server Resource Manager

Windows Server 2019 には、サービスの開始時に、ファイルサーバーリソースマネージャーサービスがすべてのボリュームに変更ジャーナル (USN ジャーナルとも呼ばれます) を作成しないようにする機能が含まれています。 これにより、各ボリューム上の領域を節約できますが、リアルタイムのファイル分類は無効になります。 詳細については、「[ファイル サーバー リソース マネージャーの概要](fsrm/fsrm-overview.md)」を参照してください。

## <a name="whats-new-in-storage-in-windows-server-version-1803"></a>Windows Server での記憶域の新機能、バージョン1803

### <a name="file-server-resource-manager"></a>File Server Resource Manager

Windows Server バージョン1803には、サービスの開始時に、ファイルサーバーリソースマネージャーサービスがすべてのボリュームに変更ジャーナル (USN ジャーナルとも呼ばれます) を作成しないようにする機能が含まれています。 これにより、各ボリューム上の領域を節約できますが、リアルタイムのファイル分類は無効になります。 詳細については、「[ファイル サーバー リソース マネージャーの概要](fsrm/fsrm-overview.md)」を参照してください。

## <a name="whats-new-in-storage-in-windows-server-version-1709"></a>Windows Server での記憶域の新機能、バージョン1709

Windows Server バージョン1709は、Semi-Annual チャネルの最初の Windows Server リリースです。 Semi-Annual チャネルはソフトウェアアシュアランスの特典であり、実稼働環境では18か月間、6か月ごとに完全にサポートされています。

詳しくは、「[Windows Server の半期チャネルの概要](../get-started-19/servicing-channels-19.md)」をご覧ください。

### <a name="storage-replica"></a>記憶域レプリカ

記憶域レプリカによって追加されたディザスターリカバリー保護が拡張され、次のものが含まれるようになりました。

- **テスト フェールオーバー**: 宛先の記憶域をマウントするオプションが、テスト フェールオーバー機能によって可能になりました。 レプリケートされた記憶域のスナップショットを、宛先ノードで、テストやバックアップの目的で、一時的にマウントすることができます。 詳細については、「[記憶域レプリカについてよく寄せられる質問](./storage-replica/storage-replica-frequently-asked-questions.md)」をご覧ください。
- **Windows 管理センターのサポート**: サーバーマネージャーツールを使用して、Windows 管理センターでレプリケーションのグラフィカル管理をサポートできるようになりました。 これには、サーバー間のレプリケーション、クラスター間のレプリケーション、およびストレッチクラスターレプリケーションが含まれます。

記憶域レプリカには、次の機能強化も含まれています。

-   自動フェールオーバーが発生するように、非同期ストレッチクラスターの動作を変更します。
-   複数のバグ修正

### <a name="smb"></a>SMB

- **SMB1 とゲスト認証の削除**: Windows Server バージョン 1709 では、SMB1 クライアントとサーバーが既定でインストールされなくなりました。 さらに、SMB2 以降のゲストとして認証する機能は、既定で無効になっています。 詳細については、[Windows 10 バージョン 1709 および Windows Server 1709 のバージョンで、SMBv1 が 既定でインストールされない問題に関するページ](https://support.microsoft.com/help/4034314/smbv1-is-not-installed-by-default-in-windows-10-rs3-and-windows-server)をご覧ください。

- **SMB2/SMB3 のセキュリティと互換性**: レガシ アプリケーションについて SMB2+ の oplock を無効にする機能や、クライアントからの接続ごとに署名や暗号化を要求する機能など、セキュリティやアプリケーションの互換性のための新しいオプションが追加されました。 詳細については、SMBShare PowerShell モジュールのヘルプを確認してください。

### <a name="data-deduplication"></a>データ重複除去

- **データ重複除去で ReFS をサポート**: ReFS による最新ファイル システムの長所とデータ重複除去のいずれかを選択する必要がなくなりました。ReFS を有効にしているときにいつでもデータ重複除去を有効にできるようになりました。 ReFS によって記憶域の効率が 95% 以上向上します。
- **重複除去されたボリュームへの最適化された送受信のための DataPort API**: 開発者は、データ重複除去によって効率的にデータを保存する方法に関する知識を活用して、ボリューム、サーバー、クラスター間で効率的にデータを移動することができます。

## <a name="whats-new-in-storage-in-windows-server-2016"></a>Windows Server 2016 での記憶域の新機能

### <a name="storage-spaces-direct"></a><a name="s2d"></a>記憶域スペース ダイレクト
記憶域スペース ダイレクトでは、ローカル記憶域を持つサーバーを使用して高可用性を備えた拡張性の高い記憶域を作成できます。 ソフトウェア定義ストレージ システムの展開と管理を簡素化し、SATA SSD や NVMe ディスク デバイスなどの新しいクラスのディスク デバイスを使用できるようにします。これは、共有ディスクを使用したクラスター記憶域スペースによるこれまでの環境では実現できませんでした。

**この変更の利点**
記憶域スペース ダイレクトによってサービス プロバイダーと企業は、ローカル記憶域を装備した業界標準サーバーを使用して、高可用性を備えた拡張性の高いソフトウェア定義ストレージを構築できます。 ローカル記憶域を装備したサーバーを使用すると複雑性が減少し、スケーラビリティが向上します。また、これまで使用できなかった記憶装置を使用でき、たとえば、SATA ソリッド ステート ディスクを使用してフラッシュ ストレージのコストを削減したり、NVMe ソリッド ステート ディスクを使用してパフォーマンスを向上したりできます。

記憶域スペース ダイレクトでは、共有 SAS ファブリックの必要性をなくしており、展開と構成が簡略化しています。 代わりに、高速で低待機時間、CPU の効率を高める記憶域として SMB3 および SMB ダイレクト (RDMA) を利用しながら、ネットワークを記憶域ファブリックとして使用します。 スケールアウトするには、サーバーを追加して記憶域容量と i/o パフォーマンスを向上させるだけで、詳細については、「 [Windows Server 2016 の記憶域スペースダイレクト](storage-spaces/storage-spaces-direct-overview.md)」を参照してください。

**動作の相違点**
この機能は Windows Server 2016 での新規です。

### <a name="storage-replica"></a><a name="storage-replica"></a>記憶域レプリカ

記憶域レプリカでは、サイト間でフェールオーバー クラスターを拡大できるだけでなく、障害復旧用に、サーバー間またはクラスター間で記憶域にとらわれずにブロックレベルで同期レプリケーションを行うことができます。 同期レプリケーションは、クラッシュ前後の整合性が維持されるボリュームを使用した物理サイト内のデータのミラーリングを実現して、ファイル システム レベルでデータがまったく失われないようにします。 非同期レプリケーションでは、データが失われる可能性はありますが、大都市圏の範囲を超えてサイトを拡張できます。

**この変更の利点**
記憶域レプリケーションでは、次の操作を行うことができます。

* ミッション クリティカルなワークロードの計画的な停止および想定外の停止のために単一ベンダー障害回復ソリューションを提供する。
* 信頼性、スケーラビリティ、パフォーマンスの点で実証済みの SMB3 トランスポートを使用する。
* 大都市圏の距離まで Windows フェールオーバー クラスターを拡大する。
* 記憶域とクラスタリングに、Hyper-V、記憶域レプリカ、記憶域スペース、クラスター、スケールアウト ファイル サーバー、SMB3、重複除去、ReFS/NTFS などの Microsoft ソフトウェアをエンド ツー エンドで使用する。
* 次のように、コストと複雑さの軽減に役立てる。
    * ハードウェアに依存せず、DAS、SAN などの特定の記憶域構成が不要です。
    * 汎用的な記憶域やネットワーク テクノロジを使用できます。
    * フェールオーバー クラスター マネージャーを通じて個々のノードとクラスターをグラフィカルに簡単に管理できます。
    * Windows PowerShell を使った包括的な大規模なスクリプト作成オプションを組み込みます。
* ダウンタイムを短縮し、Windows に備わっている信頼性と生産性の向上に役立てる。
* サポート性、パフォーマンス メトリック、および診断機能を提供する。

詳細については、[Windows Server 2016 での記憶域レプリカ](storage-replica/storage-replica-overview.md)に関する記事を参照してください。

**動作の相違点**
この機能は Windows Server 2016 での新規です。

### <a name="storage-quality-of-service"></a><a name="storage-qos"></a>記憶域のサービスの品質 (QoS)
記憶域のサービスの品質 (QoS) を使用して、Windows Server 2016 でエンド ツー エンドの記憶域のパフォーマンスを一元的に監視すると共に、Hyper-V クラスターと CSV クラスターを使用してポリシーを作成できるようになりました。

**この変更の利点**
CSV クラスターで記憶域の QoS ポリシーを作成し、Hyper-V 仮想マシンの仮想ディスク (複数可) にそのポリシーを割り当てることができるようになりました。 記憶域のパフォーマンスは、ワークロードと記憶域の負荷の変動に従って、ポリシーに合わせて自動的に再調整されます。

* 各ポリシーでは、仮想ハード ディスク、単一の仮想マシンまたは仮想マシンのグループ、サービス、テナントなどのデータ フローのコレクションに適用する設定の下限や上限を指定できます。
* Windows PowerShell または WMI を使用して、次のタスクを実行できます。
    * CSV クラスターでポリシーを作成する。
    * CSV クラスター上で使用可能なポリシーを列挙する。
    * Hyper-V 仮想マシンの仮想ハード ディスクにポリシーを割り当てる。
    * 各ワークフローのパフォーマンスとポリシー内での状態を監視する。
* 複数の仮想ハード ディスクが同じポリシーを共有している場合、パフォーマンスは、ポリシーの最小設定と最大設定の範囲内で要求を満たすように均等に分散されます。 このため、1 つのポリシーで、1 つの仮想ハード ディスク、1 つの仮想マシン、サービスを構成する複数の仮想マシン、テナントが所有するすべての仮想マシンを管理できます。

**動作の相違点**
この機能は Windows Server 2016 での新規です。 Windows Server の過去のリリースでは、下限値を管理したり、1 つのコマンドでクラスター全体の仮想ディスクすべてのフローを監視したり、ポリシーに基づいて一元的に管理したりすることはできませんでした。

詳細については、「[記憶域のサービスの品質](storage-qos/storage-qos-overview.md)」を参照してください。

### <a name="data-deduplication"></a><a name="dedup"></a>データ重複除去
| 機能 | 新機能か更新された機能か | 説明 |
|---------------|----------------|-------------|
| [大容量ボリュームのサポート](data-deduplication/whats-new.md#large-volume-support) | 更新済み | Windows Server 2016 の前までは、予期される変更量に合わせてボリュームのサイズを具体的に設定する必要がありました。そして、10 TB 以上のサイズのボリュームは重複除去に適した候補ではありませんでした。 Windows Server 2016 では、データ重複除去は **最大 64 TB** のボリュームサイズをサポートしています。 |
| [大きなファイルのサポート](data-deduplication/whats-new.md#large-file-support) | 更新済み | Windows Server 2016 の前では、1 TB に近いサイズのファイルは重複除去に適した候補ではありませんでした。 Windows Server 2016 では、 **1 TB まで** のファイルが完全にサポートされています。 |
| [Nano Server のサポート](data-deduplication/whats-new.md#nano-server-support) | 新規作成 | Windows Server 2016 の新しい Nano Server 展開オプションでは、データ重複除去が利用可能で、完全にサポートされています。 |
| [簡略化されたバックアップのサポート](data-deduplication/whats-new.md#simple-backup-support) | 新規作成 | Windows Server 2012 R2 では、Microsoft の [Data Protection Manager](/previous-versions/system-center/system-center-2012-R2/hh758173(v=sc.12)) などの仮想化されたバックアップ アプリケーションは、一連の手動による構成手順を実行することでサポートされていました。 Windows Server 2016 では、仮想化されたバックアップ アプリケーション用にデータ重複除去をシームレスに展開するために、使用法の種類の新しい既定値として "バックアップ" が追加されました。 |
| [クラスター OS のローリング アップグレードのサポート](data-deduplication/whats-new.md#cluster-upgrade-support) | 新規作成 | データ重複除去では、Windows Server 2016 の新機能である、[クラスター OS のローリング アップグレード](..//failover-clustering/cluster-operating-system-rolling-upgrade.md)が完全にサポートされています。 |

### <a name="smb-hardening-improvements-for-sysvol-and-netlogon-connections"></a><a name="smb-hardening-improvements"></a>SYSVOL と NETLOGON 接続に関する SMB セキュリティ強化の向上
Active Directory ドメイン サービスへの Windows 10 および Windows Server 2016 のクライアント接続で、ドメイン コント ローラー上の既定の SYSVOL と NETLOGON 共有では、SMB 署名と相互認証 (Kerberos など) を必要とするようになりました。

**この変更の利点**
この変更は、man-in-the-middle 攻撃の可能性を軽減します。

**動作の相違点**
SMB 署名と相互認証が使用できない場合、Windows 10 または Windows Server 2016 のコンピューターでは、ドメイン ベースのグループ ポリシーやスクリプトを処理しません。

> [!NOTE]
> これらの設定のレジストリ値は既定では存在しませんが、セキュリティ強化の規則は、グループ ポリシーまたはその他のレジストリ値でオーバーライドされるまで引き続き適用されます。

UNC ハードニングとも呼ばれる、これらのセキュリティ機能強化の詳細については、マイクロソフト サポート技術情報の記事 [3000483](https://support.microsoft.com/kb/3000483) および「[MS15-011 & MS15-014: Hardening Group Policy (MS15-011 & MS15-014: グループ ポリシーのセキュリティ強化)](https://msrc-blog.microsoft.com/2015/02/10/ms15-011-ms15-014-hardening-group-policy)」を参照してください。

### <a name="work-folders"></a>作業フォルダー
ワークフォルダーサーバーが Windows Server 2016 を実行していて、ワークフォルダークライアントが Windows 10 の場合、変更通知が改善されました。

**この変更の利点**<br>
Windows Server 2012 R2 では、ワーク フォルダー サーバーにファイルの変更が同期されるときに、クライアントには変更についての通知が送られず、変更内容が反映されるまでに最大で 10 分かかっていました。  Windows Server 2016 を使用している場合、ワークフォルダーサーバーは直ちに Windows 10 クライアントに通知し、ファイルの変更は直ちに同期されます。

**動作の相違点**<br>
この機能は Windows Server 2016 での新規です。 この機能を使用するには、Windows Server 2016 ワーク フォルダー サーバーが必須であり、またクライアントは Windows 10 である必要があります。

古いクライアントを使用しているか、ワーク フォルダー サーバーが Windows Server 2012 R2 である場合、クライアントでは引き続き 10 分ごとに変更を取得します。

### <a name="refs"></a>ReFS
新しい ReFS では、データの信頼性、回復性、スケーラビリティを実現し、さまざまなワークロードに対応した大規模な記憶域の展開がサポートされます。

**この変更の利点**<br>
ReFS では、以下の点が強化されています。

* ReFS は、新しい記憶域階層の機能を実装しており、高速なパフォーマンスと記憶域容量の増加を実現できます。 この新しい機能では、次のことを実行できます。
    * 同じ仮想ディスクで回復性の種類を複数使用する (たとえば、パフォーマンス階層でミラーリングを使用し、容量階層でパリティを使用します)。
    * 変動するワーキング セットに対する応答性を向上。
* ブロックの複製が導入され、VM の操作 (.vhdx チェックポイントのマージ操作など) のパフォーマンスが大幅に向上します。
* 新しい ReFS スキャン ツールを使用すると、損傷している記憶域の回復が可能になり、重要な破損からデータを復旧できます。

**動作の相違点**<br>
これらの機能は、Windows Server 2016 での新機能です。

## <a name="additional-references"></a>その他の参照情報
* [Windows Server 2016 の新機能](../get-started/whats-new-in-windows-server-2016.md)
