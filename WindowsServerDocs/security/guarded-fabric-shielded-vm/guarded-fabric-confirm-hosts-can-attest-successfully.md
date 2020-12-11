---
title: 保護されたホストが証明できることを確認する
description: '詳細情報: 保護されたホストが証明できることを確認する'
ms.topic: article
ms.assetid: 7485796b-b840-4678-9b33-89e9710fbbc7
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 09/25/2019
ms.openlocfilehash: 88741fcb0f10018cacb358db8a43eb6292f48811
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049830"
---
# <a name="confirm-guarded-hosts-can-attest"></a>保護されたホストが証明できることを確認する

>適用対象: windows server 2019、Windows Server (半期チャネル)、Windows Server 2016

ファブリック管理者は、Hyper-v ホストを保護されたホストとして実行できることを確認する必要があります。 少なくとも1つの保護されたホストで、次の手順を実行します。

1. Hyper-v の役割とホストガーディアンの Hyper-v サポート機能をまだインストールしていない場合は、次のコマンドを使用してインストールします。

    ```powershell
    Install-WindowsFeature Hyper-V, HostGuardian -IncludeManagementTools -Restart
    ```

2. Hgs サーバーで、Hyper-v ホストが HGS DNS 名を解決し、ポート 80 (または、HTTPS を設定している場合は 443) に接続できることを確認します。

3. ホストのキーの保護と構成証明の Url を構成します。

    - **Windows powershell を使用** する: 管理者特権の windows powershell コンソールで次のコマンドを実行して、キーの保護と構成証明の url を構成できます。 FQDN の場合 &lt; &gt; は、hgs クラスターの完全修飾ドメイン名 (fqdn) を使用します (たとえば、hgs サーバーで **HgsServer** コマンドレットを実行して、url を取得するように hgs 管理者に指示します)。

        ```PowerShell
        Set-HgsClientConfiguration -AttestationServerUrl 'http://<FQDN>/Attestation' -KeyProtectionServerUrl 'http://<FQDN>/KeyProtection'
         ```

        フォールバック HGS サーバーを構成するには、このコマンドを繰り返し、キーの保護と構成証明サービスのフォールバック Url を指定します。 詳細については、「 [フォールバック構成](guarded-fabric-manage-branch-office.md#fallback-configuration)」を参照してください。

    - **Vmm から**: SYSTEM CENTER VIRTUAL MACHINE MANAGER (vmm) を使用している場合は、vmm で構成証明とキー保護の url を構成できます。 詳細については、「 **VMM で保護** されたホストのプロビジョニング」の「[グローバル HGS 設定を構成する](/system-center/vmm/guarded-deploy-host#configure-global-hgs-settings)」を参照してください。

    >**メモ**
    > - Hgs 管理者が [hgs サーバーで HTTPS を有効](guarded-fabric-configure-hgs-https.md)にした場合は、で url を開始し `https://` ます。
    > - Hgs 管理者が HGS サーバーで HTTPS を有効にし、自己署名証明書を使用している場合は、すべてのホストの信頼されたルート証明機関ストアに証明書をインポートする必要があります。 これを行うには、各ホストで次のコマンドを実行します。
       ```PowerShell
       Import-Certificate -FilePath "C:\temp\HttpsCertificate.cer" -CertStoreLocation Cert:\LocalMachine\Root
       ```
    > - HTTPS を使用するように HGS クライアントを構成し、TLS 1.0 システム全体を無効にしている場合は、[最新の tls ガイダンス](guarded-fabric-troubleshoot-hosts.md#modern-tls)を参照してください。

4. ホストで構成証明の試行を開始して、構成証明の状態を表示するには、次のコマンドを実行します。

    ```powershell
    Get-HgsClientConfiguration
    ```

    コマンドの出力は、ホストが構成証明を受けたかどうかを示し、現在は保護されています。 `IsHostGuarded`が **True** を返さない場合は、HGS 診断ツール [HgsTrace](https://technet.microsoft.com/library/mt718831.aspx)を実行して調査できます。 診断を実行するには、ホストの管理者特権の Windows PowerShell プロンプトで次のコマンドを入力します。

    ```powershell
    Get-HgsTrace -RunDiagnostics -Detailed
    ```

    > [!IMPORTANT]
    > Windows Server 2019 または Windows 10 バージョン1809以降を使用していて、コード整合性ポリシーを使用している場合は、 `Get-HgsTrace` **コード整合性ポリシーアクティブ** 診断の失敗を返します。
    > 失敗した診断が唯一の場合は、この結果を無視しても問題ありません。

## <a name="next-step"></a>次の手順

> [!div class="nextstepaction"]
> [シールドされた VMの展開](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)

## <a name="additional-references"></a>その他の参照情報

- [Deploy the Host Guardian Service (HGS) (ホスト ガーディアン サービス (HGS) の展開)](guarded-fabric-deploying-hgs-overview.md)
- [シールドされた VMの展開](guarded-fabric-configuration-scenarios-for-shielded-vms-overview.md)
