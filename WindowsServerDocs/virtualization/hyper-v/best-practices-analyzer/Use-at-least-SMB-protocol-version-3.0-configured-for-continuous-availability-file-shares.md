---
title: 仮想マシンのファイルを格納するファイル共有での継続的な可用性を実現するように構成された SMB プロトコルバージョン3.0 以降を使用する
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: a1fa5cf9-8a48-4f63-bb57-d81e63e77b30
ms.date: 8/16/2016
ms.openlocfilehash: 9e913ac96075d7ad15d4e50872e52aa3c863ac5a
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746797"
---
# <a name="use-at-least-smb-protocol-version-30-configured-for-continuous-availability-on-file-shares-that-store-files-for-virtual-machines"></a>仮想マシンのファイルを格納するファイル共有での継続的な可用性を実現するように構成された SMB プロトコルバージョン3.0 以降を使用する

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*バーチャルマシンファイルまたはバーチャルハードディスクファイルは、SMB プロトコルバージョン3.0 の継続的可用性機能が構成されていないネットワークファイル共有に保管されます。*

## <a name="impact"></a>**影響**
*この構成は、サーバーを使用した仮想マシンの可用性に影響を与える可能性があるため、Microsoft は推奨しません。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
次のいずれかの操作を行います。

-   継続的な可用性を確保するように構成されている SMB 3.0 ファイル共有にファイルを移動します。

-   現在のファイル共有を再構成して、継続的な可用性を提供します。



