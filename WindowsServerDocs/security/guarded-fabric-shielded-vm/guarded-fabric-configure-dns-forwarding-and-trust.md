---
description: 詳細については、「HGS ドメインで DNS 転送を構成する」および「ファブリックドメインとの一方向の信頼」を参照してください。
title: DNS 転送とドメイン信頼を構成する
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 2031c7f56c96764a716f29afc4f0cfe27c452646
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97040370"
---
# <a name="configure-dns-forwarding-in-the-hgs-domain-and-a-one-way-trust-with-the-fabric-domain"></a>HGS ドメインで DNS 転送を構成し、ファブリックドメインとの一方向の信頼を構成する

>適用先:Windows Server (半期チャネル)、Windows Server 2016

>[!IMPORTANT]
>AD モードは、Windows Server 2019 以降では非推奨とされます。 TPM の構成証明が不可能な環境では、 [ホストキー](guarded-fabric-initialize-hgs-key-mode.md)の構成証明を構成します。 ホストキーの構成証明により、AD モードと同様の保証が提供され、セットアップが簡単になります。

次の手順を使用して、DNS 転送を設定し、ファブリックドメインとの一方向の信頼を確立します。 これらの手順により、HGS はファブリックドメインコントローラーを検索し、Hyper-v ホストのグループメンバーシップを検証することができます。

1.  管理者特権の PowerShell セッションで次のコマンドを実行して、DNS 転送を構成します。 Fabrikam.com をファブリックドメインの名前に置き換え、ファブリックドメイン内の DNS サーバーの IP アドレスを入力します。 高可用性を実現するには、複数の DNS サーバーをポイントします。

    ```powershell
    Add-DnsServerConditionalForwarderZone -Name "fabrikam.com" -ReplicationScope "Forest" -MasterServers <DNSserverAddress1>, <DNSserverAddress2>
    ```

2.  一方向のフォレストの信頼を作成するには、管理者特権のコマンドプロンプトで次のコマンドを実行します。

    を `bastion.local` HGS ドメインの名前で、を `fabrikam.com` ファブリックドメインの名前に置き換えます。 ファブリックドメインの管理者のパスワードを指定します。

    ```powershell
    netdom trust bastion.local /domain:fabrikam.com /userD:fabrikam.com\Administrator /passwordD:<password> /add
    ```

## <a name="next-step"></a>次の手順

> [!div class="nextstepaction"]
> [HTTPS の構成](guarded-fabric-configure-hgs-https.md)
