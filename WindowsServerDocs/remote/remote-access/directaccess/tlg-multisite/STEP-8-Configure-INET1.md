---
title: 手順 8. INET1 を構成する
description: このトピックは、「Windows Server 2016 用の DirectAccess マルチサイト展開のテストラボガイド」の一部です。
ms.topic: article
ms.assetid: 693acb5c-dffc-4484-8286-163bb67724c9
ms.author: lizross
author: eross-msft
manager: mtillman
ms.openlocfilehash: eed2aef3cf1104d070feb43c37243a92e48e5206
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89636760"
---
# <a name="step-8-configure-inet1"></a>手順 8: INET1 を構成する

>適用先:Windows Server (半期チャネル)、Windows Server 2016

クライアントコンピューターがインターネット経由でリモートアクセスサーバーに接続できるようにするには、INET1 で EDGE1 の DNS エントリを構成する必要があります。

### <a name="to-create-the-2-edge1-dns-entry"></a>2 EDGE1 DNS エントリを作成するには

1.  **スタート**画面で「**dnsmgmt.msc**」と入力し、enter キーを押します。

2.  コンソールツリーで、[ **前方参照ゾーン**] を開き、[ **contoso.com**] をクリックします。次に、[ **contoso.com**] を右クリックし、[ **新しいホスト (A または AAAA)**] をクリックします。

3.  [ **名前**] に「 **2-EDGE1**」と入力します。 [ **IP アドレス**] に、「 **131.107.0.20**」と入力します。 [**ホストの追加**] をクリックし、[**OK**] をクリックして、[**完了**] をクリックします。



