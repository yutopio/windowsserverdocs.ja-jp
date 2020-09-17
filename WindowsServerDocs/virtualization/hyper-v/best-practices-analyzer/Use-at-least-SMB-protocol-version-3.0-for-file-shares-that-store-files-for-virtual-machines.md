---
title: バーチャルマシンのファイルを保存するファイル共有には、SMB プロトコルバージョン3.0 以降を使用してください。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 4bb832b8-f1aa-4c1f-a0f2-324dd53553ea
ms.date: 8/16/2016
ms.openlocfilehash: a979035c5b58542865faf6254baf49815f81cc2d
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746787"
---
# <a name="use-at-least-smb-protocol-version-30-for-file-shares-that-store-files-for-virtual-machines"></a>バーチャルマシンのファイルを保存するファイル共有には、SMB プロトコルバージョン3.0 以降を使用してください。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|エラー|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*仮想マシンファイルまたは仮想ハードディスクファイルは、SMB プロトコルバージョン3.0 以降をサポートしていないファイル共有に格納されます。*

## <a name="impact"></a>**影響**
*Microsoft では、この構成をサポートしていません。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*SMB プロトコルバージョン3.0 以降を使用しているファイル共有にファイルを移動します。*



