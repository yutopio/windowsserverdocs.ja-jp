---
title: Hyper-v VHD セットファイルの作成
description: Hyper-v 2016 で VHDset ファイルを作成する手順
author: jiwool
ms.author: jiwool
ms.date: 01/26/2017
ms.topic: article
ms.assetid: 444e1496-9e5a-41cf-bfbc-306e2ed8e00a
ms.openlocfilehash: bc49260471394ab1efd342fa51b8649b680b2851
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96865801"
---
# <a name="create-hyper-v-vhd-set-files"></a>Hyper-v VHD セットファイルの作成
VHD セットファイルは、Windows Server 2016 のゲストクラスター用の新しい共有仮想ディスクモデルです。 VHD セットファイルは、共有仮想ディスクのオンラインサイズ変更をサポートし、Hyper-v レプリカをサポートします。また、アプリケーション整合性チェックポイントに含めることができます。

VHD セットファイルは、新しい VHD ファイルの種類を使用します。Vhd. VHD セットファイルは、ゲストクラスターで使用されるグループ仮想ディスクに関するチェックポイント情報をメタデータの形式で格納します。

Hyper-v では、チェックポイントチェーンの管理と共有 VHD セットのマージのすべての側面が処理されます。 管理ソフトウェアでは、の場合と同じように、VHD セットファイルのオンラインサイズ変更などのディスク操作を実行できます。VHDX ファイル。 これは、管理ソフトウェアが VHD セットのファイル形式について認識する必要がないことを意味します。

> [!NOTE]
> 運用環境に展開する前に、VHD セットファイルの影響を評価することが重要です。 ディスクの待機時間など、環境にパフォーマンスや機能が低下していないことを確認します。

## <a name="create-a-vhd-set-file-from-hyper-v-manager"></a>Hyper-v マネージャーからの VHD セットファイルの作成

1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、**[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。
2.  [操作] ウィンドウで [ **新規作成**] をクリックし、[ **ハードディスク**] をクリックします。
3.  [ **ディスクフォーマットの選択** ] ページで、バーチャルハードディスクの形式として [ **VHD Set** ] を選択します。
4.  ウィザードのページに進み、バーチャルハードディスクをカスタマイズします。 [ **次へ** ] をクリックしてウィザードの各ページを移動するか、左ペインでページの名前をクリックすると、そのページに直接移動できます。
5.  バーチャルハードディスクの構成が完了したら、[ **完了**] をクリックします。

## <a name="create-a-vhd-set-file-from-windows-powershell"></a>Windows PowerShell からの VHD セットファイルの作成

ファイルの種類を使用して、 [新しい VHD](/powershell/module/hyper-v/new-vhd) コマンドレットを使用します。ファイルパス内の VHD。 この例では、10 Gb の base .vhd という名前の VHD セットファイルを作成します。

``` PowerShell
PS c:\>New-VHD -Path c:\base.vhds -SizeBytes 10GB
```

## <a name="migrate-a-shared-vhdx-file-to-a-vhd-set-file"></a>共有 VHDX ファイルを VHD セットファイルに移行する

既存の共有 VHDX を VHD に移行するには、VM をオフラインにする必要があります。 Windows PowerShell を使用した推奨プロセスは次のとおりです。

1. VHDX を VM から削除します。 たとえば、以下を実行します。
   ``` PowerShell
   PS c:\>Remove-VMHardDiskDrive existing.vhdx
   ```

2. VHDX を VHD に変換します。 たとえば、以下を実行します。
   ``` PowerShell
   PS c:\>Convert-VHD existing.vhdx new.vhds
   ```

3. VHD を VM に追加します。 たとえば、以下を実行します。
   ``` PowerShell
   PS c:\>Add-VMHardDiskDrive new.vhds
   ```
