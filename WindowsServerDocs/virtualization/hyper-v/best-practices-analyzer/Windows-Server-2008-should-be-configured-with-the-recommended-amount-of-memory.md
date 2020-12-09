---
title: Windows Server 2008 は、推奨されるメモリ量で構成する必要があります。
description: このベストプラクティスアナライザー規則によって報告された問題を解決するための手順を示します。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: a98a8594-603b-487a-8739-78887c568e57
ms.date: 8/16/2016
ms.openlocfilehash: d712ca14527fec503d8767ac08e608fdf325cfe9
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96865861"
---
# <a name="windows-server-2008-should-be-configured-with-the-recommended-amount-of-memory"></a>Windows Server 2008 は、推奨されるメモリ量で構成する必要があります。

>適用先:Windows Server 2016

ベスト プラクティスとスキャンの詳細については、「 [ベスト プラクティス アナライザー](https://go.microsoft.com/fwlink/?LinkId=122786)」をご覧ください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題

*Windows Server 2008 を実行している仮想マシンは、推奨される RAM 容量 (2 GB) 未満で構成されています。*

## <a name="impact"></a>影響

*ゲストオペレーティングシステムとアプリケーションが正常に動作しない可能性があります。複数のアプリケーションを同時に実行するのに十分なメモリがない可能性があります。これは、次の仮想マシンに影響します。*

\<list of virtual machine names>

## <a name="resolution"></a>解決方法

*Hyper-v マネージャーを使用して、この仮想マシンに割り当てられているメモリを少なくとも 2 GB に増やします。*

### <a name="increase-the-memory-using-hyper-v-manager"></a>Hyper-v マネージャーを使用してメモリを増やす

1.  Hyper-V マネージャーを開きます。 **[スタート]** ボタンをクリックし、**[管理ツール]** をポイントして **[Hyper-V マネージャー]** をクリックします。

2.  結果ウィンドウで [ **仮想マシン**, 、構成する仮想マシンを選択します。 バーチャルマシンの状態は [ **オフ (オフ**)」と表示されます。 そうでない場合は、バーチャルマシンを右クリックし、[ **シャットダウン**] をクリックします。

3.  **[操作]** ウィンドウで、仮想マシン名の下の **[設定]** をクリックします。

4.  ナビゲーションウィンドウで、[ **メモリ**] をクリックします。

5.  [ **メモリ** ] ページで、 **スタートアップ RAM** を 2 GB 以上に設定し、[ **OK]** をクリックします。

### <a name="increase-memory-using-windows-powershell"></a>Windows PowerShell を使用してメモリを増やす

1.  Windows PowerShell を開きます。 (デスクトップから [ **スタート** ] をクリックし、「 **Windows PowerShell**」と入力を開始します)。

2.  右クリック **Windows PowerShell** ] をクリック **管理者として実行** します。

3.  次のようなコマンドを実行し \<MyVM> ます。を仮想マシンの名前に、を少なくとも以下の値に置き換えます。

```
Set-VMMemory <MyVM> -StartupBytes 2GB
```

## <a name="see-also"></a>関連項目
[設定-VMMemory](/powershell/module/hyper-v/set-vmmemory)
