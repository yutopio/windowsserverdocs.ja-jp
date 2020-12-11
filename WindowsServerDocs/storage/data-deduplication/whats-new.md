---
description: 詳細については、「データ重複除去の新機能」を参照してください。
ms.assetid: d11acbc2-40c6-4ab2-9514-2bc3ad81499a
title: データ重複除去の新機能します。
ms.topic: article
author: wmgries
manager: klaasl
ms.author: wgries
ms.date: 04/17/2019
ms.openlocfilehash: a33a248c8fce180b6ffe3de335fa876829ae05a9
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97048470"
---
# <a name="whats-new-in-data-deduplication"></a>データ重複除去の新機能します。

> 適用先:Windows Server 2019、Windows Server 2016、Windows Server (半期チャネル)

Windows Server での[データ重複除去](overview.md)は、プライベートクラウドのスケールで、パフォーマンスと柔軟性が高く、管理しやすいように最適化されています。 Windows Server のソフトウェアで定義された記憶域スタックの詳細については、「 [Windows server の記憶域の新機能](../whats-new-in-storage.md)」を参照してください。

Windows Server 2019 では、データ重複除去の機能が次のように強化されています。

| 機能 | 新規/更新 | 説明 |
|---------------|----------------|-------------|
| ReFS のサポート  | 新規作成            | 同じボリューム上に、ReFS ファイルシステムの重複除去と圧縮を使用して最大10倍のデータを格納します。 ( [1 回クリックするだけ](https://www.youtube.com/watch?v=PRibTacyKko&feature=youtu.be) で、Windows 管理センターで有効にすることができます)。オプションの圧縮を使用した可変サイズのチャンクストアでは、節約率が最大になりますが、マルチスレッドの後処理アーキテクチャではパフォーマンスに影響を最小限に抑えることができます。 は、最大 64 TB のボリュームをサポートし、各ファイルの最初の 4 TB を重複除去します。|

データ重複除去では、Windows Server 2016 以降、次の点が強化されています。

| 機能 | 新規/更新 | 説明 |
|---------------|----------------|-------------|
| [大量ボリュームのサポート](whats-new.md#large-volume-support) | 更新済み | Windows Server 2016 以前では、想定されるチャーンに合わせてボリュームのサイズを具体的に設定する必要があり、10 TB を超えるサイズのボリュームは重複除去に適していませんでした。 Windows Server 2016 のデータ重複除去では、最大 64 TB のボリューム サイズがサポートされます。 |
| [大きなファイルのサポート](whats-new.md#large-file-support) | 更新済み | Windows Server 2016 の前では、1 TB に近いサイズのファイルは重複除去に適した候補ではありませんでした。 Windows Server 2016 では、1 TB までのファイルが完全にサポートされます。 |
| [Nano Server のサポート](whats-new.md#nano-server-support) | 新規作成 | Windows Server 2016 の新しい Nano Server 展開オプションでは、データ重複除去が利用可能で、完全にサポートされています。 |
| [バックアップ サポートの簡略化](whats-new.md#simple-backup-support) | 新規作成 | Windows Server 2012 R2 では、Microsoft の [Data Protection Manager](/previous-versions/system-center/system-center-2012-R2/hh758173(v=sc.12)) などの仮想化バックアップ アプリケーションをサポートするには、一連の手動による構成手順を実行する必要がありました。 Windows Server 2016 では、仮想化バックアップ アプリケーションに対してデータ重複除去をシームレスに展開するために、使用法の種類の新しい既定値 (バックアップ) が追加されました。|
| [クラスター OS のローリング アップグレードのサポート](whats-new.md#cluster-upgrade-support) | 新規作成 | データ重複除去では、Windows Server 2016 の新機能である、[クラスター OS のローリング アップグレード](../..//failover-clustering/cluster-operating-system-rolling-upgrade.md)が完全にサポートされています。 |

## <a name="support-for-large-volumes"></a><a name="large-volume-support"></a>大量ボリュームのサポート

**この変更の利点**
Windows Server 2012 R2 でデータ重複除去のパフォーマンスを最適化するには、最適化ジョブがデータ変化の速度 ("チャーン") に対応できるように、ボリュームのサイズを適切に設定する必要がありました。 すなわち、ワークロードの書き込みパターンによっても異なりますが、通常は、ボリューム が 10 TB 以下でなければデータ重複除去で高いパフォーマンスを達成できません。

Windows Server 2016 では、ボリューム 64 TB までのデータ重複除去で非常に高いパフォーマンスを達成できます。

**動作の相違点**
Windows Server 2012 R2 のデータ重複除去ジョブ パイプラインでは、ボリュームごとにシングル スレッドと I/O キューが使用されます。 最適化ジョブが遅れてボリュームの全体的な削減率が低下しないようにするには、大きいデータセットを小さいボリュームに分割する必要があります。 適切なボリュームのサイズは、そのボリュームで予想されるチャーンに応じて決まります。 最大サイズの平均は、チャーンが高いボリュームでは約 6 - 7 TB、チャーンが低いボリュームでは約 9 - 10 TB です。

Windows Server 2016 では、データ重複除去ジョブのパイプラインの設計が見直され、ボリュームごとに複数の I/O キューを使用して複数のスレッドを並列実行するようになりました。 これにより、以前は小さいボリュームにデータを分割しなければ得られなかったパフォーマンスを、分割することなく達成できるようになりました。 この変更を次の図に示します。

![Windows Server 2012 R2 と Windows Server 2016 のデータ重複除去ジョブ パイプラインの比較の視覚化](media/server-2016-dedup-job-pipeline.png)

これらの最適化は、最適化ジョブだけでなく、[すべてのデータ重複除去ジョブ](understand.md#job-info)に適用されます。

## <a name="support-for-large-files"></a><a name="large-file-support"></a>大きなファイルのサポート
**この変更の利点**
Windows Server 2012 R2 では、非常に大きなファイルは、重複除去処理パイプラインのパフォーマンス低下を引き起こすことから、データ重複除去に適していません。 Windows Server 2016 では、1 TB までのファイルの重複除去を非常に高いパフォーマンスで実行できることから、管理者はさまざまなワークロードで重複除去による削減を実現できます。 たとえば、バックアップ ワークロードに通常付随する非常に大きなファイルの重複除去を行うことができます。

**動作の相違点**
Windows Server 2016 のデータ重複除去では、新しいストリーム マップ構造とその他の "内部" の改良により、最適化のスループットとアクセス パフォーマンスが向上しています。 さらに、重複除去処理パイプラインでは、フェールオーバー後に最適化を再び実行するのではなく、再開することができるようになりました。 これらの変更によって、1 TB までのファイルの重複除去が非常に高パフォーマンスとなっています。

## <a name="support-for-nano-server"></a><a name="nano-server-support"></a>Nano Server のサポート
**この変更の利点**
Nano Server は、Windows Server 2016 の新しいヘッドレス展開オプションです。Windows Server Core の展開オプションと比べて、必要なシステム リソースのフットプリントが極めて小さくなり、起動にかかる時間が大幅に短縮されるとともに、更新と再起動の回数が少なくてすみます。 Nano Server ではデータ重複除去が完全にサポートされています。 Nano Server の詳細については、[Nano Server の概要](../../get-started/getting-started-with-nano-server.md)に関するページを参照してください。

## <a name=""></a><a name="simple-backup-support">仮想化されたバックアップアプリケーションの構成の簡略化</a>
**この変更の利点**
Windows Server 2012 R2 では、仮想化バックアップ アプリケーションのデータ重複除去はサポートされていますが、重複除去設定を手動でチューニングする必要があります。 Windows Server 2016 では、仮想化バックアップ アプリケーションの構成が大幅に簡略化されています。 ボリュームの重複除去を有効にする際に、汎用ファイル サーバーと VDI の場合と同様に、事前定義済みの使用方法の種類オプションを使用して構成を行うことができます。

## <a name=""></a><a name="cluster-upgrade-support">クラスター OS のローリング アップグレードのサポート</a>
**この変更の利点**
データ重複除去を実行している Windows Server フェールオーバー クラスターで、Windows Server 2012 R2 バージョンのデータ重複除去を実行しているノードと、Windows Server 2016 バージョンのデータ重複除去を実行しているノードを混在させることができます。 この機能強化により、クラスター ローリング アップグレード中に、重複除去対象のすべてのボリュームへの完全なデータ アクセスが可能になり、すべてのノードを一括でアップグレードするためのダウンタイムを発生させずに、既存の Windows Server 2012 R2 クラスターに新しいバージョンのデータ重複除去を段階的にロールアウトできます。

**動作の相違点**<br />
Windows Server の以前のバージョンでは、Windows Server フェールオーバー クラスター内にあるすべてのノードの Windows Server バージョンを同じにする必要がありました。 Windows Server 2016 以降は、クラスター ローリング アップグレード機能により、クラスターを混在モードで実行できるようになりました。 データ重複除去ではこの新しい混在モードのクラスター構成がサポートされており、クラスター ローリング アップグレード中の完全なデータ アクセスが可能になりました。
