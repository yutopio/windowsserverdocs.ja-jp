---
title: 仮想ネットワークの使用状況測定の送信
description: クラウドネットワーク収益化の基本的な側面は、ネットワーク帯域幅の送信です。 たとえば、Microsoft Azure ビジネスモデルでの送信データ転送。 送信データは、特定の請求サイクルで、インターネット経由で Azure データセンターから移動されるデータの合計量に基づいて課金されます。
manager: grcusanz
ms.topic: get-started-article
ms.author: anpaul
author: AnirbanPaul
ms.date: 10/02/2018
ms.openlocfilehash: a9e939b4a810848e91b5d2cb8e4b878bbcf56e84
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156462"
---
# <a name="egress-metering-in-a-virtual-network"></a>仮想ネットワークの使用状況測定の送信

>適用対象:Windows Server 2019


クラウドネットワーク収益化の基本的な側面は、ネットワーク帯域幅の使用量によって課金できるようになっています。 送信データは、特定の請求サイクルにおいて、インターネット経由でデータセンターから移動されるデータの総量に基づいて課金されます。

Windows Server 2019 の SDN ネットワークトラフィックの送信測定機能を使用すると、送信データ転送の使用量メーターを提供できます。 各仮想ネットワークを離れたネットワークトラフィックは、データセンター内に保持されるため、個別に追跡することで、課金の計算から除外することができます。 未請求のいずれかのアドレス範囲に含まれていない宛先 IP アドレスにバインドされたパケットは、送信データ転送の課金として追跡されます。

## <a name="virtual-network-unbilled-address-ranges-allowlist-of-ip-ranges"></a>仮想ネットワークの未請求のアドレス範囲 (IP 範囲の許可リスト)

未請求のアドレス範囲は、既存の仮想ネットワークの "非 **実体** 化" プロパティの下にあります。 既定では、アドレス範囲は追加されていません。

   ```PowerShell
   import-module NetworkController
   $uri = "https://sdn.contoso.com"

   (Get-NetworkControllerVirtualNetwork -ConnectionURI $URI -ResourceId "VNet1").properties
   ```

出力は次のようになります。
   ```
    AddressSpace           : Microsoft.Windows.NetworkController.AddressSpace
    DhcpOptions            :
    UnbilledAddressRanges  :
    ConfigurationState     :
    ProvisioningState      : Succeeded
    Subnets                : {21e71701-9f59-4ee5-b798-2a9d8c2762f0, 5f4758ef-9f96-40ca-a389-35c414e996cc,
                         29fe67b8-6f7b-486c-973b-8b9b987ec8b3}
    VirtualNetworkPeerings :
    EncryptionCredential   :
    LogicalNetwork         : Microsoft.Windows.NetworkController.LogicalNetwork
   ```


## <a name="example-manage-the-unbilled-address-ranges-of-a-virtual-network"></a>例: 仮想ネットワークの未請求アドレス範囲を管理する

仮想ネットワークの "非ユーザー設定" プロパティを設定することに **より、請求** された送信測定から除外する IP サブネットプレフィックスのセットを管理できます。  仮想ネットワーク上のネットワークインターフェイスによって送信された、プレフィックスのいずれかに一致する宛先 IP アドレスを持つトラフィックは、BilledEgressBytes プロパティに含まれません。

1.  アクセスに対して課金されないサブネットが含まれるように、"非 **実体** 化" プロパティを更新します。

    ```PowerShell
    $vnet = Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceID "VNet1"
    $vnet.Properties.UnbilledAddressRanges = "10.10.2.0/24,10.10.3.0/24"
    ```

    >[!TIP]
    >複数の IP サブネットを追加する場合は、各 IP サブネット間にコンマを使用します。  コンマの前または後にスペースを入れないでください。

2.  **"変更**されていない" プロパティを使用して、Virtual Network リソースを更新します。

    ```PowerShell
    New-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceId "VNet1" -Properties $unbilled.Properties -PassInnerException
    ```

    出力は次のようになります。
      ```
         Confirm
         Performing the operation 'New-NetworkControllerVirtualNetwork' on entities of type
         'Microsoft.Windows.NetworkController.VirtualNetwork' via
         'https://sdn.contoso.com/networking/v3/virtualNetworks/VNet1'. Are you sure you want to continue?
         [Y] Yes  [N] No  [S] Suspend  [?] Help (default is "Y"): y


         Tags             :
         ResourceRef      : /virtualNetworks/VNet1
         InstanceId       : 29654b0b-9091-4bed-ab01-e172225dc02d
         Etag             : W/"6970d0a3-3444-41d7-bbe4-36327968d853"
         ResourceMetadata :
         ResourceId       : VNet1
         Properties       : Microsoft.Windows.NetworkController.VirtualNetworkProperties
      ```


3. Virtual Network を確認して、構成されていない **アドレス範囲**を確認します。

   ```PowerShell
   (Get-NetworkControllerVirtualNetwork -ConnectionUri $uri -ResourceID "VNet1").properties
   ```

   出力は次のようになります。
   ```
   AddressSpace           : Microsoft.Windows.NetworkController.AddressSpace
   DhcpOptions            :
   UnbilledAddressRanges  : 10.10.2.0/24,192.168.2.0/24
   ConfigurationState     :
   ProvisioningState      : Succeeded
   Subnets                : {21e71701-9f59-4ee5-b798-2a9d8c2762f0, 5f4758ef-9f96-40ca-a389-35c414e996cc,
                        29fe67b8-6f7b-486c-973b-8b9b987ec8b3}
   VirtualNetworkPeerings :
   EncryptionCredential   :
   LogicalNetwork         : Microsoft.Windows.NetworkController.LogicalNetwork
   ```

## <a name="check-the-billed-the-unbilled-egress-usage-of-a-virtual-network"></a>仮想ネットワークの未請求送信の使用量の請求を確認する

"未請求" プロパティ **を構成** した後、仮想ネットワーク内の各サブネットの請求および送信の使用状況を確認できます。 送信トラフィックは、課金対象と未請求範囲の合計バイト数で4分ごとに更新されます。

各仮想サブネットでは、次のプロパティを使用できます。

-   **UnbilledEgressBytes** は、この仮想サブネットに接続されているネットワークインターフェイスによって送信された未請求バイト数を示します。 未請求 bytes は、親仮想ネットワークの "非 **実体** 化" プロパティの一部であるアドレス範囲に送信されるバイト数です。

-   **BilledEgressBytes** は、この仮想サブネットに接続されているネットワークインターフェイスによって送信された、課金されたバイト数を示します。 課金されるバイト数は、親仮想ネットワーク **の "非** " 特性の値に含まれていないアドレス範囲に送信されたバイト数です。

次の例を使用して、送信の使用状況をクエリします。

```PowerShell
(Get-NetworkControllerVirtualNetwork -ConnectionURI $URI -ResourceId "VNet1").properties.subnets.properties | ft AddressPrefix,BilledEgressBytes,UnbilledEgressBytes
```

出力は次のようになります。
```
AddressPrefix BilledEgressBytes UnbilledEgressBytes
------------- ----------------- -------------------
10.0.255.8/29          16827067                   0
10.0.2.0/24           781733019                   0
10.0.4.0/24                   0                   0
```


---
