---
title: Microsoft Online Service パートナー契約の登録パートナー情報の追加
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: 9bd191d6-ecc5-4230-a88e-f3fc281cb956
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 807aacc5039bf90ea4dd7c7859c232d8c8b3011a
ms.sourcegitcommit: 34f9577ef32cbdc7ef96040caabc9d83517f9b79
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/08/2020
ms.locfileid: "89554345"
---
# <a name="add-microsoft-online-service-partner-agreement-partner-of-record-information"></a>Microsoft Online Service パートナー契約の登録パートナー情報の追加

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

##  <a name="BKMK_3rdLevelDomanNames"></a>
 Microsoft 365 の Microsoft Online Service パートナー契約 (MOSPA) パートナーは、Microsoft 365 統合モジュールを使用して Windows Server Essentials からサブスクリプション要求が発生したときに正しく補正されるようにするには、取引先レコード id (POR ID) を含むレジストリキーを作成する必要があります。 次の情報が読み取られ、Microsoft 365 のサインアップ Url を使用してサービスプロバイダーに渡されます。

-   HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows Server\MSO

-   種類 = 文字列値

-   キー名 = Partner

-   値 = xxxxx (xxxxx は POR ID)

#### <a name="to-add-the-por-id-key-to-the-registry"></a>POR ID キーをレジストリに追加するには

1.  参照コンピューターで [**スタート**] をクリックし、「**regedit**」と入力して、Enter キーを押します。

2.  左のウィンドウで、[**HKEY_LOCAL_MACHINE**]、[**SOFTWARE**]、[**Microsoft**]、[**Windows Server**] の順に展開します。

3.  [**Windows Server**] を右クリックし、[**新規作成**] をクリックして、[**キー**] をクリックします。

4.  キーの名前には「**MSO**」と入力します。

5.  先ほど作成したキーを右クリックし、[**文字列値**] をクリックします。

6.  文字列の名前に「**Partner**」と入力して、Enter キーを押します。

7.  右側のウィンドウで、新しい **Partner** 文字列を右クリックし、[**変更**] をクリックします。

8.  [**値のデータ**] ボックスに POR ID を入力し、[**OK**] をクリックします。

## <a name="see-also"></a>参照

 [イメージの作成とカスタマイズ追加の](Creating-and-Customizing-the-Image.md)[カスタマイズ](Additional-Customizations.md)[展開のイメージの準備](Preparing-the-Image-for-Deployment.md)[カスタマーエクスペリエンスのテスト](Testing-the-Customer-Experience.md)

