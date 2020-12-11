---
description: 詳細については、「クラスターのパフォーマンス履歴」を参照してください。
title: クラスターのパフォーマンス履歴
ms.author: cosdar
manager: eldenc
ms.topic: article
author: cosmosdarwin
ms.date: 02/02/2018
ms.localizationpriority: medium
ms.openlocfilehash: 14e2c493b4d93268d7d3e458c3cd3b2f53de1e1f
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97046170"
---
# <a name="performance-history-for-clusters"></a>クラスターのパフォーマンス履歴

> 適用対象:Windows Server 2019

[記憶域スペースダイレクトのパフォーマンス履歴](performance-history.md)のこのサブトピックでは、クラスターに対して収集されたパフォーマンス履歴について説明します。

クラスターレベルで生成されたシリーズはありません。 代わりに、などのサーバーシリーズ `clusternode.cpu.usage` がクラスター内のすべてのサーバーに対して集計されます。 ボリュームシリーズ (など) `volume.iops.total` は、クラスター内のすべてのボリュームに対して集計されます。 また、などのドライブシリーズ `physicaldisk.size.total` は、クラスター内のすべてのドライブに対して集計されます。

## <a name="usage-in-powershell"></a>PowerShell での使用法

[Get クラスター](/powershell/module/failoverclusters/get-cluster)コマンドレットを使用します。

```PowerShell
Get-Cluster | Get-ClusterPerf
```

## <a name="additional-references"></a>その他の参照情報

- [記憶域スペース ダイレクトのパフォーマンス履歴](performance-history.md)
