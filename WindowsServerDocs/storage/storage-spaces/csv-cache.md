---
description: 詳細については、CSV インメモリ読み取りキャッシュでの記憶域スペースダイレクトの使用に関するページを参照してください。
title: メモリ内読み取りキャッシュの記憶域スペースダイレクト
ms.author: eldenc
manager: siroy
ms.topic: article
author: eldenchristensen
ms.date: 09/21/2020
ms.localizationpriority: medium
ms.openlocfilehash: abda5d2bfeb5bcf65c66609c1e89ab2371089330
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97040530"
---
# <a name="using-storage-spaces-direct-with-the-csv-in-memory-read-cache"></a>CSV インメモリ読み取りキャッシュでの記憶域スペースダイレクトの使用

> 適用先:Windows Server 2019、Windows Server 2016

このトピックでは、システムメモリを使用して [記憶域スペースダイレクト](storage-spaces-direct-overview.md)のパフォーマンスを向上させる方法について説明します。

記憶域スペースダイレクトは、メモリ内の読み取りキャッシュクラスターの共有ボリューム (CSV) と互換性があります。 システム メモリを使用して読み取りをキャッシュすると、バッファーなし I/O を使用して VHD または VHDX ファイルにアクセスする Hyper-V などのアプリケーションのパフォーマンスを向上させることができます。 (バッファリングされていない IOs とは、Windows キャッシュマネージャーによってキャッシュされない操作のことです)。

メモリ内キャッシュはサーバーローカルであるため、ハイパー集約記憶域スペースダイレクト配置のデータの局所性が向上します。最近の読み取りは、仮想マシンが実行されているのと同じホスト上のメモリにキャッシュされるので、ネットワーク経由での読み取り回数を減らすことができます。 この結果、待機時間が短くなり、ストレージのパフォーマンスが向上します。

## <a name="planning-considerations"></a>計画に関する考慮事項

インメモリ読み取りキャッシュは、仮想デスクトップ インフラストラクチャ (VDI) など、大量の読み取りが発生するワークロードで最も効果的です。 反対に、ワークロードで書き込みが極めて大量に発生する場合は、キャッシュによってその価値を上回るオーバーヘッドが発生する場合があるため、キャッシュは無効にする必要があります。

CSV インメモリ読み取りキャッシュ用に、物理メモリの合計の最大 80% を使用できます。

  > [!TIP]
  > コンピューティングとストレージが同じサーバー上で実行されるハイパー収束デプロイの場合は、仮想マシン用に十分なメモリを確保するように注意してください。 収束 Scale-Out ファイルサーバー (SoFS) の展開では、メモリの競合が少ないため、これは適用されません。

  > [!NOTE]
  > DISKSPD や [VM Fleet](https://github.com/Microsoft/diskspd/tree/master/Frameworks/VMFleet) など、一部のマイクロベンチマーク ツールでは、CSV インメモリ読み取りキャッシュがない場合より、有効になっている場合に、より悪い結果が出ることがあります。 既定では、VM は仮想マシンごとに 1 10 ギビバイト (GiB) の VHDX を作成し、100 vm では約 1 TiB の合計を作成した後、 *一様にランダム* な読み取りと書き込みを実行します。 実際のワークロードとは異なり、読み取りは予測可能なパターンまたは反復パターンに従わないため、インメモリ キャッシュは効果がなく、オーバーヘッドが発生します。

## <a name="configuring-the-in-memory-read-cache"></a>インメモリ読み取りキャッシュを構成する

CSV インメモリ読み取りキャッシュは、Windows Server 2019 と Windows Server 2016 で同じ機能を使用して利用できます。 Windows Server 2019 では、既定では1つの GiB が割り当てられています。 Windows Server 2016 では、既定ではオフになっています。

| OS バージョン             | 既定の CSV キャッシュ サイズ           |
|------------------------|----------------------------------|
| Windows Server 2019    | 1 GiB                            |
| Windows Server 2016    | 0 (無効)                     |
| Windows Server 2012 R2 | 有効-ユーザーはサイズを指定する必要があります |
| Windows Server 2012    | 0 (無効)                     |

PowerShell を使用して割り当てられているメモリの量を確認するには、以下を実行します。

```PowerShell
(Get-Cluster).BlockCacheSize
```

返される値は、サーバーあたりのメビバイト (MiB) 数です。 たとえば、は `1024` 1 ギビバイト (GiB) を表します。

割り当てられているメモリの量を変更するには、PowerShell を使用してこの値を変更します。 たとえば、サーバーあたり 2 GiB を割り当てるには、以下を実行します。

```PowerShell
(Get-Cluster).BlockCacheSize = 2048
```

変更をただちに有効にするために、CSV ボリュームを一時停止して再開するか、サーバー間で移動します。 たとえば、次の PowerShell フラグメントを使用して、各 CSV を別のサーバー ノードに移動し、再び戻します。

```PowerShell
Get-ClusterSharedVolume | ForEach {
    $Owner = $_.OwnerNode
    $_ | Move-ClusterSharedVolume
    $_ | Move-ClusterSharedVolume -Node $Owner
}
```

## <a name="additional-references"></a>その他の参照情報

- [記憶域スペース ダイレクトの概要](storage-spaces-direct-overview.md)
