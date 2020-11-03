---
title: を使用してネットワークコントローラーのサーバーの役割をインストールサーバーマネージャー
description: このトピックでは、Windows Server 2016 のサーバーマネージャーを使用して、ネットワークコントローラーのサーバーの役割をインストールする手順について説明します。
manager: grcusanz
ms.topic: get-started-article
ms.assetid: 3a6e4352-ff62-4290-b8a4-5c83740070fc
ms.author: anpaul
author: AnirbanPaul
ms.openlocfilehash: cdaf8f294322c4108152ca5bd622f5346f7618f7
ms.sourcegitcommit: 8c0a419ae5483159548eb0bc159f4b774d4c3d85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/03/2020
ms.locfileid: "93235839"
---
# <a name="install-the-network-controller-server-role-using-server-manager"></a>を使用してネットワークコントローラーのサーバーの役割をインストールサーバーマネージャー

> 適用先:Windows Server (半期チャネル)、Windows Server 2016

このトピックでは、サーバー マネージャーを使用して、ネットワーク コント ローラー サーバーの役割をインストールする方法の手順を示します。

> [!IMPORTANT]
> ネットワーク コントローラー サーバー ロールを物理ホストに展開しないでください。 ネットワークコントローラーを展開するに \( は、hyper-v ホストにインストールされている hyper-v 仮想マシン VM にネットワークコントローラーサーバーの役割をインストールする必要があり \) ます。 3つの異なる Hyper-v ホスト上の Vm にネットワークコントローラーをインストールした後 \- 、 \- \( \) Windows PowerShell コマンド **NetworkControllerServer** を使用してネットワークコントローラーにホストを追加することで、ソフトウェア定義ネットワーク SDN 用の hyper-v ホストを有効にする必要があります。 これにより、SDN ソフトウェア ロード バランサーを機能させることができます。 詳細については、「 [NetworkControllerServer](https://docs.microsoft.com/powershell/module/networkcontroller/new-networkcontrollerserver)」を参照してください。

ネットワーク コント ローラーをインストールした後は、追加のネットワーク コント ローラー構成の Windows PowerShell コマンドを使用する必要があります。 詳細については、次を参照してください。 [展開ネットワーク コント ローラーが Windows PowerShell を使用して](../../deploy/Deploy-Network-Controller-using-Windows-PowerShell.md)します。

### <a name="to-install-network-controller"></a>ネットワーク コント ローラーをインストールするには

1. サーバー マネージャーで、[ **管理** ] をクリックし、[ **役割と機能の追加** ] をクリックします。 役割と機能の追加ウィザードが開きます。 **[次へ]** をクリックします。

2. **[インストールの種類** , 既定の設定を保持し、クリックして **次** します。

3. **移行先サーバーの選択** , 、ネットワーク コント ローラーをインストールするサーバーを選択して **次** します。

4. **[サーバーの役割** , で、 **ロール** , をクリックして **ネットワーク コント ローラー** します。

    ![ネットワーク コント ローラーのサーバーの役割](../../../media/Install-the-Network-Controller-server-role-using-Server-Manager/netc_install_07.jpg)

5. **ネットワーク コント ローラーに必要な機能を追加** ] ダイアログ ボックスが表示されます。 **[機能の追加]** をクリックします。

    ![ネットワーク コント ローラーの機能を追加します。](../../../media/Install-the-Network-Controller-server-role-using-Server-Manager/netc_install_06.jpg)

6. [ **サーバーの役割の選択** ] で、[ **次へ** ] をクリックします。

    ![[Next]\(次へ\) をクリックします](../../../media/Install-the-Network-Controller-server-role-using-Server-Manager/netc_install_07.jpg)

7. [ **機能の選択** ] で、[ **次へ** ] をクリックします。

8. **ネットワーク コント ローラー** クリックして **次** します。

9. **インストール オプションの確認** , 、選択内容を確認します。 ネットワーク コント ローラーのインストールでは、ウィザードを実行した後、コンピューターを再起動する必要があります。 このため、次のようにクリックします。 **ために必要な場合は、移行先サーバーを自動的に再起動** します。 **追加の役割と機能ウィザード** ] ダイアログ ボックスが表示されます。 **[はい]** をクリックします。

    ![役割および機能の追加ウィザード](../../../media/Install-the-Network-Controller-server-role-using-Server-Manager/netc_install_11.jpg)

10. **[インストール オプションの確認]** で、 **[インストール]** をクリックします。

11. 移行先サーバーにネットワーク コント ローラー サーバーの役割をインストールし、サーバーを再起動します。

12. コンピューターを再起動した後、コンピューターにログオンし、サーバー マネージャーを表示してネットワーク コント ローラーのインストールを確認します。

    ![サーバー マネージャー](../../../media/Install-the-Network-Controller-server-role-using-Server-Manager/nc_013.jpg)

## <a name="see-also"></a>参照
[ネットワーク コントローラー](Network-Controller.md)
