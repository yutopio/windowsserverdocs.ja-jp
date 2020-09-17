---
title: スマートページングファイルをシステムディスクに保存しない
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 9b57c9b8-76c5-43c7-bfa6-2c95b3cb6510
ms.date: 8/16/2016
ms.openlocfilehash: c1d2a6ca3b1ffc96fb0761ab1b1c434971374142
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90747027"
---
# <a name="avoid-storing-smart-paging-files-on-a-system-disk"></a>スマートページングファイルをシステムディスクに保存しない

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|操作|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示されるテキストを示します。

## <a name="issue"></a>問題
*仮想マシンが再起動され、スマートページングファイル用に指定された場所が Hyper-v を実行するサーバーのシステムディスクである場合、1つまたは複数の仮想マシンのメモリ構成でスマートページングを使用することが必要になる場合があります。*

## <a name="impact"></a>影響
*システムディスクをスマートページングに使用すると、Hyper-v を実行しているサーバーで問題が発生する可能性があります。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策
*非システムディスクにスマートページングファイルを格納するように仮想マシンを再構成します。*



