---
title: 1つまたは2つの仮想プロセッサを使用して Windows Vista を実行する仮想マシンを構成する
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: e562bce3-fd68-42c9-821c-12022ae4746c
ms.date: 8/16/2016
ms.openlocfilehash: bf5780ae397dd774dd6063e9dcdafd36907199f4
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90744037"
---
# <a name="configure-virtual-machines-running-windows-vista-with-1-or-2-virtual-processors"></a>1つまたは2つの仮想プロセッサを使用して Windows Vista を実行する仮想マシンを構成する

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|構成|
|**カテゴリ**|エラー|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*Windows Vista を実行している仮想マシンは、2つ以上の仮想プロセッサで構成されています。*

## <a name="impact"></a>影響

*Microsoft では、次の仮想マシンの構成をサポートしていません。*

\<list of virtual machine names>

## <a name="resolution"></a>解決策

*仮想マシンをシャットダウンし、1つまたは複数の仮想プロセッサを削除します。*

### <a name="to-remove-virtual-processors"></a>仮想プロセッサを削除するには

1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、**[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。

2.  結果ウィンドウで [ **仮想マシン**, 、構成する仮想マシンを選択します。 バーチャルマシンの状態は [ **オフ (オフ**)」と表示されます。 そうでない場合は、バーチャルマシンを右クリックし、[ **シャットダウン**] をクリックします。

3.  **[操作]** ウィンドウで、仮想マシン名の下の **[設定]** をクリックします。

4.  ナビゲーションウィンドウで、[ **プロセッサ**] をクリックします。

5.  [ **プロセッサ** ] ページで、プロセッサ数を **1** または **2** に設定し、[ **OK**] をクリックします。



