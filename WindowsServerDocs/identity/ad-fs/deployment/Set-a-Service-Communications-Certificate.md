---
description: 詳細については、「サービス通信証明書を設定する」を参照してください。
ms.assetid: 638c89bd-87e6-484b-9d2e-8ae2a74227e5
title: サービス通信証明書を設定する
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 4d5991240e33d6775f7b7744775bfc4608a15f9b
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049080"
---
# <a name="set-a-service-communications-certificate"></a>サービス通信証明書を設定する


Active Directory フェデレーションサービス (AD FS) AD FS のフェデレーション \( サーバー \) は、サービス通信証明書を使用して、 \( \) web クライアントまたはフェデレーションサーバープロキシとの Secure Sockets Layer SSL 通信のために web サービストラフィックをセキュリティで保護します。

> [!NOTE]
> サービス通信証明書が SSL 証明書と同じではありません。 AD FS SSL 証明書を変更するには、Powershell を使用する必要があります。 この [記事](../operations/manage-ssl-certificates-ad-fs-wap.md)のガイダンスに従ってください。


AD FS 管理スナップインを使用してサービス通信証明書を変更するには、次の手順を実行 \- します。

> [!NOTE]
> AD FS 管理スナップインは、 \- サービス通信証明書としてのフェデレーションサーバーのサーバー認証証明書を参照します。

この手順を完了するには、ローカル コンピューター上の **Administrators** または同等のメンバーシップが最低限必要です。  適切なアカウントおよびグループメンバーシップの使用に関する詳細については、「[ローカルおよびドメインの既定のグループ](https://go.microsoft.com/fwlink/?LinkId=83477) \( http: \/ \/ go.microsoft.com fwlink?」を参照して \/ \/ ください。LinkId \= 83477 \) 。

### <a name="to-set-a-service-communications-certificate"></a>サービス通信証明書を設定するには

1.  **スタート** 画面で「**AD FS Management**」と入力し、enter キーを押します。

2.  コンソールツリーで、[サービス] をダブルクリックし、[ \- **証明書**] をクリックします。 

3.  [ **操作** ] ウィンドウで、[ **サービス通信証明書の設定** ] リンクをクリックします。

4.  [ **サービス通信証明** 書の選択] ダイアログボックスで、サービス通信証明書として設定する証明書ファイルに移動し、証明書ファイルを選択して、[ **開く**] をクリックします。

## <a name="additional-references"></a>その他のリファレンス
[チェックリスト:フェデレーション サーバーのセットアップ](Checklist--Setting-Up-a-Federation-Server.md)

[フェデレーション サーバーの証明書の要件](../design/certificate-requirements-for-federation-servers.md)
