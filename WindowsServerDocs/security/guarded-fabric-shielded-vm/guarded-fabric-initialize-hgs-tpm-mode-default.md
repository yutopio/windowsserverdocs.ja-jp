---
description: 詳細については、「新しい専用フォレストで TPM モードを使用して HGS クラスターを初期化する (既定)」を参照してください。
title: 新しい専用フォレストで TPM モードを使用して HGS クラスターを初期化する (既定)
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: eb63af4feb13b519906b8898a1eb9a352bf91d27
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97047340"
---
# <a name="initialize-the-hgs-cluster-using-tpm-mode-in-a-new-dedicated-forest-default"></a>新しい専用フォレストで TPM モードを使用して HGS クラスターを初期化する (既定)

> 適用対象: windows server 2019、Windows Server (半期チャネル)、Windows Server 2016

1.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-one.md)]

2.  [!INCLUDE [Obtain certificates for HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-two.md)]

3.  最初の HGS ノードで、管理者特権の PowerShell ウィンドウで [HgsServer](https://docs.microsoft.com/powershell/module/hgsserver/initialize-hgsserver) を実行します。 このコマンドレットの構文では、多くの異なる入力がサポートされていますが、最も一般的な2つの呼び出しは次のとおりです。

    -   署名証明書と暗号化証明書に PFX ファイルを使用している場合は、次のコマンドを実行します。

        ```powershell
        $signingCertPass = Read-Host -AsSecureString -Prompt "Signing certificate password"
        $encryptionCertPass = Read-Host -AsSecureString -Prompt "Encryption certificate password"

        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificatePath '.\signCert.pfx' -SigningCertificatePassword $signingCertPass -EncryptionCertificatePath '.\encCert.pfx' -EncryptionCertificatePassword $encryptionCertPass -TrustTpm
        ```

    -   ローカル証明書ストアにインストールされているエクスポートできない証明書を使用している場合は、次のコマンドを実行します。 証明書の拇印がわからない場合は、を実行して、使用可能な証明書を一覧表示でき `Get-ChildItem Cert:\LocalMachine\My` ます。

        ```powershell
        Initialize-HgsServer -HgsServiceName 'MyHgsDNN' -SigningCertificateThumbprint '1A2B3C4D5E6F...' -EncryptionCertificateThumbprint '0F9E8D7C6B5A...' -TrustTpm
        ```

4.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-four.md)]

5.  [!INCLUDE [Initialize HGS](../../../includes/guarded-fabric-initialize-hgs-default-step-five.md)]

## <a name="next-step"></a>次の手順

> [!div class="nextstepaction"]
> [TPM ルート証明書のインストール](guarded-fabric-install-trusted-tpm-root-certificates.md)
