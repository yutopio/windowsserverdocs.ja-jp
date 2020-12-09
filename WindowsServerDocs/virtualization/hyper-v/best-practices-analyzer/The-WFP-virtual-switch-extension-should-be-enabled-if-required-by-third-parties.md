---
title: 'The WFP virtual switch extension should be enabled if it is required by third party extensions (Hyper-V: サード パーティ製の拡張機能で必要とされている場合、WFP 仮想スイッチ拡張機能を有効にする必要がある)'
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 8aa8a9a5-e3fa-4c9b-8331-ba5a3de22429
ms.date: 8/16/2016
ms.openlocfilehash: 00312413c8da02ce5221767667ecd941f0095776
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96865161"
---
# <a name="the-wfp-virtual-switch-extension-should-be-enabled-if-it-is-required-by-third-party-extensions"></a>The WFP virtual switch extension should be enabled if it is required by third party extensions (Hyper-V: サード パーティ製の拡張機能で必要とされている場合、WFP 仮想スイッチ拡張機能を有効にする必要がある)

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
*Windows フィルタ リング プラットフォーム (WFP) の仮想スイッチ拡張機能は無効です。*

## <a name="impact"></a>**影響**
*次の仮想スイッチでは、いくつかサード パーティ製の仮想スイッチ拡張機能が正常に動作しない可能性があります。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*サード パーティ製の拡張機能に必要な場合は、Windows フィルタ リング プラットフォームを有効にするのにには、有効にする-VMSwitchExtension である Windows PowerShell コマンドレットを使用します。*

### <a name="enable-the-windows-filtering-platform-using-windows-powershell"></a>Windows PowerShell を使用して Windows フィルタ リング プラットフォームを有効にします。

1.  Windows PowerShell を開きます。 (デスクトップから [ **スタート** ] をクリックし、「 **Windows PowerShell**」と入力を開始します)。

2.  右クリック **Windows PowerShell** ] をクリック **管理者として実行** します。

3.  外部スイッチの名前の外部を交換した後、このコマンドを実行します。

```
Enable-VMSwitchExtension -VMSwitchName External -Name Microsoft Windows Filtering Platform
```

## <a name="see-also"></a>関連項目
[有効にする VMSwitchExtension](/powershell/module/hyper-v/enable-vmswitchextension)
