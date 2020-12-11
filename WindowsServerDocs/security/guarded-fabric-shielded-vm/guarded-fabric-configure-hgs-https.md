---
description: 詳細については、「HTTPS 通信用に HGS を構成する」を参照してください。
title: HTTPS 通信用に HGS を構成する
ms.topic: article
manager: dongill
author: rpsqrd
ms.author: ryanpu
ms.date: 08/29/2018
ms.openlocfilehash: c28500d236625410961ef1ee3012001c1d277714
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049890"
---
# <a name="configure-hgs-for-https-communications"></a>HTTPS 通信用に HGS を構成する

>適用対象: windows server 2019、Windows Server (半期チャネル)、Windows Server 2016

既定では、HGS サーバーを初期化すると、IIS web サイトは HTTP 専用通信用に構成されます。
HGS との間で送受信されるすべての機密情報は、常にメッセージレベルの暗号化を使用して暗号化されますが、高いレベルのセキュリティが求められる場合は、HGS を SSL 証明書で構成して HTTPS を有効にすることもできます。

[!INCLUDE [Configure HTTPS](../../../includes/configure-hgs-for-https.md)]

