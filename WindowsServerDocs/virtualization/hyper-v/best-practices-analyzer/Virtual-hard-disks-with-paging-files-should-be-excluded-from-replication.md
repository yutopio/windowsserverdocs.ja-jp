---
title: 仮想ハード_ディスクのページング ファイルとは、レプリケーションから除外する必要があります。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: c0be8a5f-64a1-488a-944e-bb913bb90517
ms.date: 8/16/2016
ms.openlocfilehash: 14729113ee2ba3694bcc29d50da5e7113c763268
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746567"
---
# <a name="virtual-hard-disks-with-paging-files-should-be-excluded-from-replication"></a>仮想ハード_ディスクのページング ファイルとは、レプリケーションから除外する必要があります。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|Information|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*ページング ファイルは、レプリケーションに参加しているから除外する必要がありますが、ディスクが除外されません。*

## <a name="impact"></a>影響
*ページングファイルを使用すると、大量の入出力アクティビティが発生し、レプリケーションに参加するために必要なリソースが不必要に増えることがあります。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*Windows のページングファイル用に別の仮想ハードディスクを作成していない場合は、作成します。初期レプリケーションが既に完了している場合は、Hyper-v マネージャーを使用してレプリケーションを削除します。次に、レプリケーションをもう一度構成し、ページングファイルのある仮想ハードディスクをレプリケーションから除外します。*



