---
title: ゲストオペレーティングシステムでサポートされている場合にのみ SCSI コントローラーを構成する
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 861f194f-467e-4b07-a1c5-55b35f6327c4
ms.date: 8/16/2016
ms.openlocfilehash: cadf4c0d0ce8cdd50d66a61f428b3e547dd457dc
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746997"
---
# <a name="configure-scsi-controllers-only-when-supported-by-the-guest-operating-system"></a>ゲストオペレーティングシステムでサポートされている場合にのみ SCSI コントローラーを構成する

>適用先:Windows Server 2016



|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*ゲストオペレーティングシステムが SCSI コントローラーをサポートしていないため、バーチャルマシンには使用できない SCSI コントローラーが構成されています。*

## <a name="impact"></a>影響

*バーチャルマシンは、SCSI コントローラーに接続された記憶域を使用できません。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>解決策

*バーチャルマシンをシャットダウンし、Hyper-v マネージャーを使用してバーチャルマシンから SCSI コントローラーを削除します。次に、仮想マシンを再起動します。*



