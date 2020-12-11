---
description: '詳細情報: 管理者によって信頼された構成証明を使用して HGS を初期化する'
title: 管理者に信頼された構成証明を使用して HGS を初期化する
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 65ba0bd90d42ac038eeb8eb304def80ce7093ff1
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049760"
---
# <a name="initialize-hgs-using-admin-trusted-attestation"></a>管理者に信頼された構成証明を使用して HGS を初期化する

>適用先:Windows Server (半期チャネル)、Windows Server 2016

>[!IMPORTANT]
>管理者によって信頼された構成証明 (AD モード) は、Windows Server 2019 以降では非推奨とされます。 TPM の構成証明が不可能な環境では、 [ホストキー](guarded-fabric-initialize-hgs-key-mode.md)の構成証明を構成します。 ホストキーの構成証明により、AD モードと同様の保証が提供され、セットアップが簡単になります。


これらの手順は、新しいフォレストまたは既存の要塞フォレストで HGS を初期化するかどうかによって異なります。

1. [新しいフォレストで HGS クラスターを初期化する (既定)](guarded-fabric-initialize-hgs-ad-mode-default.md)

   または

   [既存の要塞フォレストの HGS クラスターを初期化する](guarded-fabric-initialize-hgs-ad-mode-bastion.md)

2. [ファブリックドメインで DNS 転送を構成する](guarded-fabric-configuring-fabric-dns.md)

3. [DNS 転送と HGS ドメインでの一方向の信頼の構成](guarded-fabric-configure-dns-forwarding-and-trust.md)



