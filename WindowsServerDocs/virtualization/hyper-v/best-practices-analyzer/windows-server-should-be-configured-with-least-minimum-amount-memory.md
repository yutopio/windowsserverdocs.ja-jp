---
title: Windows Server 2016 にする必要があります最小メモリ量以上で構成
description: このベストプラクティスアナライザー規則によって報告された問題を解決するための手順を示します。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: d324af73-af73-40b0-bd5b-8003ba3e921b
ms.date: 8/16/2016
ms.openlocfilehash: 7b1aeb2a8fcc6ac499946a5c9364775222b34d26
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746107"
---
# <a name="windows-server-2016-should-be-configured-with-at-least-the-minimum-amount-of-memory"></a>Windows Server 2016 にする必要があります最小メモリ量以上で構成

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
*Windows Server 2016 を実行する仮想マシンは、512 mb の RAM の最小量よりも少ないリソースで構成されます。*

## <a name="impact"></a>**影響**
*次の仮想マシン上のゲストオペレーティングシステムが実行されていないか、または信頼性の高い動作をしていない可能性があります。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*Hyper-v マネージャーを使用して、この仮想マシンに割り当てられているメモリを少なくとも 512 MB に増やします。*

#### <a name="increase-the-memory-using-hyper-v-manager"></a>Hyper-v マネージャーを使用してメモリを増やす

1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、**[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。

2.  結果ウィンドウで [ **仮想マシン**, 、構成する仮想マシンを選択します。 バーチャルマシンの状態は [ **オフ (オフ**)」と表示されます。 そうでない場合は、バーチャルマシンを右クリックし、[ **シャットダウン**] をクリックします。

3.  **[操作]** ウィンドウで、仮想マシン名の下の **[設定]** をクリックします。

4.  ナビゲーションウィンドウで、[ **メモリ**] をクリックします。

5.  [ **メモリ** ] ページで、 **スタートアップ RAM** を 512 MB 以上に設定し、[ **OK]** をクリックします。

### <a name="increase-the-memory-using-windows-powershell"></a>Windows PowerShell を使用してメモリを増やす

1.  Windows PowerShell を開きます。 (デスクトップから [ **スタート** ] をクリックし、「 **Windows PowerShell**」と入力を開始します)。

2.  右クリック **Windows PowerShell** ] をクリック **管理者として実行**します。

3.  交換した後にこのコマンドを実行 \<MyVM> 、仮想マシンの名前に置き換えます。

```
Set-VMMemory <MyVM> -StartupBytes 512MB
```

## <a name="see-also"></a>関連項目
[設定-VMMemory](/powershell/module/hyper-v/set-vmmemory?view=win10-ps)