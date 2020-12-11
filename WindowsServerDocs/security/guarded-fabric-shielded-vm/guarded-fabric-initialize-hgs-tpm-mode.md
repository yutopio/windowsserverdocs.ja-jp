---
description: 詳細については、TPM を使用した HGS の初期化-信頼された構成証明
title: TPM の信頼された構成証明を使用して HGS を初期化する
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: 6dc4139b1204242a96b99e93d211a673756bdc5a
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049740"
---
# <a name="initialize-hgs-using-tpm-trusted-attestation"></a>TPM の信頼された構成証明を使用して HGS を初期化する

>適用対象: windows server 2019、Windows Server (半期チャネル)、Windows Server 2016

これらの手順は、新しいフォレストまたは既存の要塞フォレストで HGS を初期化するかどうかによって異なります。

1. [新しいフォレストで HGS クラスターを初期化する (既定)](guarded-fabric-initialize-hgs-tpm-mode-default.md)

   または

   [既存の要塞フォレストの HGS クラスターを初期化する](guarded-fabric-initialize-hgs-tpm-mode-bastion.md)

2. [信頼された TPM ルート証明書をインストールする](guarded-fabric-install-trusted-tpm-root-certificates.md)
3. [ファブリック DNSの構成](guarded-fabric-configuring-fabric-dns.md)

