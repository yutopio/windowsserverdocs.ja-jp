---
description: 詳細については、「新しいフォレストに HGS をインストールする」を参照してください。
title: 新しいフォレストに HGS をインストールする
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 934efb699dd1c9f37219606ebc7f1b748f61eb18
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049730"
---
# <a name="install-hgs-in-a-new-forest"></a>新しいフォレストに HGS をインストールする

>適用対象: windows server 2019、Windows Server (半期チャネル)、Windows Server 2016

## <a name="add-the-hgs-server-role"></a>HGS サーバーロールを追加する

管理者特権の PowerShell セッションで次のコマンドを実行して、HGS サーバーの役割を追加し、HGS をインストールします。

[!INCLUDE [Install the HGS server role](../../../includes/guarded-fabric-install-hgs-server-role.md)]

## <a name="install-hgs"></a>HGS のインストール

[!INCLUDE [Install HGS by default](../../../includes/install-hgs-default.md)]

## <a name="next-steps"></a>次のステップ

- TPM ベースの構成証明を設定する次の手順については、「 [新しい専用フォレストで tpm モードを使用して HGS クラスターを初期化する (既定)](guarded-fabric-initialize-hgs-tpm-mode-default.md)」を参照してください。
- ホストキーの構成証明を設定する次の手順については、「 [新しい専用フォレストでキーモードを使用して HGS クラスターを初期化する (既定)](guarded-fabric-initialize-hgs-key-mode-default.md)」を参照してください。
- 管理者ベースの構成2019証明をセットアップする次の手順については、「 [新しい専用フォレストで AD モードを使用して HGS クラスターを初期化する (既定)](guarded-fabric-initialize-hgs-ad-mode-default.md)」を参照してください。

## <a name="next-step"></a>次の手順

> [!div class="nextstepaction"]
> [HGS の初期化](guarded-fabric-initialize-hgs.md)


