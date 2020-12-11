---
description: '詳細情報: 保護されたホスト (AD) のファブリック DNS を構成する'
title: 保護されたホスト (AD) のファブリック DNS を構成する
ms.topic: article
ms.assetid: 074b6d09-f16e-49bf-b88a-377139d35067
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 29ec5a824ca16b45bc4445a7d838c71985ca6457
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049870"
---
# <a name="configure-the-fabric-dns-for-guarded-hosts-ad"></a>保護されたホスト (AD) のファブリック DNS を構成する

>適用先:Windows Server 2016


>[!IMPORTANT]
>AD モードは、Windows Server 2019 以降では非推奨とされます。 TPM の構成証明が不可能な環境では、 [ホストキー](guarded-fabric-initialize-hgs-key-mode.md)の構成証明を構成します。 ホストキーの構成証明により、AD モードと同様の保証が提供され、セットアップが簡単になります。

ファブリック管理者は、保護されたホストが HGS クラスターを解決できるようにするために、ファブリック DNS が必要とする構成を行う必要があります。
Hgs クラスターは、既に [hgs 管理者によって設定](/WindowsServerDocs/virtualization/guarded-fabric-shielded-vm/guarded-fabric-setting-up-the-host-guardian-service-hgs.md)されている必要があります。



[!INCLUDE [Configure fabric DNS](../../../includes/guarded-fabric-configure-fabric-dns.md)]


## <a name="next-step"></a>次の手順

> [!div class="nextstepaction"]
> [HGS DNS と一方向の信頼の構成](guarded-fabric-configure-dns-forwarding-and-trust.md)
