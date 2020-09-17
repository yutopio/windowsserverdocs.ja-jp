---
title: レプリカ サーバーは、特定のプライマリ サーバーがレプリケーション トラフィックを送信する権限を特定するように構成する必要があります。
description: このベストプラクティスアナライザー規則によって報告された問題を解決するための手順を示します。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 0aeb1f4b-2e75-430b-9557-fe64738c4992
ms.date: 8/16/2016
ms.openlocfilehash: 68953fe3efaba64c853e4da83d4ca47ff13ca00a
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745817"
---
# <a name="replica-servers-should-be-configured-to-identify-specific-primary-servers-authorized-to-send-replication-traffic"></a>レプリカ サーバーは、特定のプライマリ サーバーがレプリケーション トラフィックを送信する権限を特定するように構成する必要があります。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*上記の構成でこのレプリカ サーバーはすべてのプライマリ サーバーからのレプリケーション トラフィックを受信し、1 つの場所に保存します。*

### <a name="impact"></a>影響
*すべてのプライマリ サーバーからのすべてのレプリケーションは、プライバシーやセキュリティ上の問題を招く可能性がありますが、1 つの場所に格納されます。*

## <a name="resolution"></a>解決策
*Hyper-v マネージャーを使用して、特定のプライマリサーバーの新しい承認エントリを作成し、それぞれに個別の記憶域の場所を指定します。ワイルドカード文字を使用すると、各承認エントリのセットにプライマリサーバーをグループ化できます。*

#### <a name="create-authorization-entries-using-hyper-v-manager"></a>HYPER-V マネージャーを使用して承認エントリを作成します。

1.  Hyper-V マネージャーを開きます。 (サーバーマネージャーから、[**ツール**  >  ] をクリックします。**Hyper-v マネージャー**)

2.  ホストの一覧から、目的のホストを右クリックし、[Hyper-v の **設定**] をクリックします。

3.  ナビゲーションウィンドウで、[ **レプリケーションの構成**] をクリックします。

4.  [ **承認と記憶域**] で、[ **指定したサーバーからレプリケーションを許可する**] をクリックします。

5.  サーバーの一覧の下にある [ **追加**] をクリックします。

6.  [ **承認エントリの追加**] で、次のようにします。

    -   最初のサーバーの完全修飾名を入力します。

    -   そのサーバーのファイルのみを格納する専用の場所を指定します。

7.  **[OK]** をクリックします。

8.  各プライマリサーバーに対してこの手順を繰り返します。

9. もう一度 [ **OK** ] をクリックして終了し、ウィンドウを閉じます。

### <a name="create-authorization-entries-using-windows-powershell"></a>Windows PowerShell を使用して承認エントリを作成する

1.  Windows PowerShell を開きます。 (デスクトップから [スタート] をクリックし、「 **Windows PowerShell**」と入力を開始します)。

2.  右クリック **Windows PowerShell** ] をクリック **管理者として実行**します。

3.  次のようなコマンドを実行して、を置き換えます。

    -   サーバーの完全修飾ドメイン名を使用した server01.domain01.contoso.com のプライマリサーバー名。

    -   D:\ReplicaVMStorage の場所を指定します。

    -   既定という名前の信頼グループが作成されている場合は、そのグループの名前。 それ以外の場合は、既定値を使用します。

```
New-VMReplicationAuthorizationEntry server01.domain01.contoso.com D:\ReplicaVMStorage DEFAULT
```

## <a name="see-also"></a>関連項目
[新しい VMReplicationAuthorizationEntry](/powershell/module/hyper-v/new-vmreplicationauthorizationentry?view=win10-ps)