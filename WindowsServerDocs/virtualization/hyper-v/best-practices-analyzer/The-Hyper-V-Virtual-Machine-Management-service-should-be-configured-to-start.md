---
title: HYPER-V 仮想マシン管理サービスは、自動的に開始するように構成する必要があります。
description: このベストプラクティスアナライザー規則によって報告された問題を解決するための手順を示します。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 222bbe76-c514-4a3f-b61b-860a4dc2826a
ms.date: 8/16/2016
ms.openlocfilehash: 8245e425adb1b1187918e9ee213135c16a190cde
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746497"
---
# <a name="the-hyper-v-virtual-machine-management-service-should-be-configured-to-start-automatically"></a>HYPER-V 仮想マシン管理サービスは、自動的に開始するように構成する必要があります。

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

*自動的に開始する HYPER-V バーチャル マシン管理サービスが構成されていません。*

## <a name="impact"></a>影響

*サービスが開始されるまで、仮想マシンを管理できません。*

実行されている仮想マシンは引き続き実行します。 ただし、仮想マシンを管理または作成またはサービスが実行されるまでは、それらを削除することはできません。

## <a name="resolution"></a>解決策

*サービス スナップインまたは sc config コマンド ライン ツールを使用して、自動的に開始するサービスを再構成します。*

> [!TIP]
> デスクトップ アプリで、サービスが見つからないか、コマンド ライン ツールをレポートしたサービスが存在しない、HYPER-V 管理ツール可能性がありますがインストールされていません。 そのインストール手順は次のとおりです。
>
> - Windows Server で、サーバー マネージャーを開き [役割と機能のウィザードを使用します。 詳細については、次を参照してください。 [Windows Server 2016 に Hyper-v の役割をインストール](../get-started/Install-the-Hyper-V-role-on-Windows-Server.md)します。
> - Windows では、デスクトップで、入力を開始 **プログラム**, 、] をクリックして **プログラムと機能** (コントロール パネル) > **に Windows の機能のオンとオフ** > **HYPER-V** > **HYPER-V 管理ツール**します。 次に、 **[OK]** をクリックします

#### <a name="to-reconfigure-the-service-to-start-automatically-using-the-services-desktop-app"></a>サービスのデスクトップ アプリを使用して自動的に開始するサービスを再構成するには

1.  サービスのデスクトップ アプリを開きます。 (をクリックして **開始**, 、検索ボックスをクリックし、入力を開始 **サービス**, 、結果の一覧の [サービス] をクリックします。

2.  詳細ペインで右クリック **HYPER-V 仮想マシン管理**, 、] をクリックし、 **プロパティ**します。

3.  **全般** ] タブの [ **スタートアップ** をクリックして、入力 **自動**です。

#### <a name="to-reconfigure-the-service-to-start-automatically-using-the-sc-config-command"></a>SC Config コマンドを使用して自動的に開始するサービスを再構成するには

1.  Windows PowerShell を開きます。

2.  型:

    ```
    set-service  vmms -startuptype automatic
    ```

3.  サービスがまだ実行されていない場合は、次のように入力します。

    ```
    start-service -name vmms
    ```



