---
description: 詳細については、「Token-Signing 証明書の追加」を参照してください。
ms.assetid: bbb84ea6-7e31-4442-85ab-a9447e7c19e8
title: トークン署名証明書を追加する
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 16db3238d8d3dcac55f228a5a9cca80ccf3ca132
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97048140"
---
# <a name="add-a-token-signing-certificate"></a>トークン署名証明書を追加する


Active Directory フェデレーションサービス (AD FS) AD FS のフェデレーションサーバーでは \( \) \- 、フェデレーションリソースへの不正アクセスを試みるために、攻撃者がセキュリティトークンを変更または偽造するのを防ぐために、トークン署名証明書が必要になります。 すべて \- のトークン署名証明書には、秘密キーによるデジタル署名に使用される暗号化秘密キーと公開キーが含まれてい \( \) ます。セキュリティトークンです。 その後、これらのキーがパートナーフェデレーションサーバーによって受信された後、 \( 暗号化されたセキュリティトークンの公開キーによって信頼性が検証され \) ます。

> [!CAUTION]
> トークンの署名に使用される証明書 \- は、フェデレーションサービスの安定性を確保するために重要です。 この目的で構成された証明書の損失または計画外の削除によってサービスが中断される可能性があるため、この目的で構成された証明書をバックアップする必要があります。

トークン \- 署名証明書は、フェデレーションサービス内の信頼されたルートにチェーンされている必要があります。 \-エクスポートしたファイルから AD FS 管理スナップインにトークン署名証明書を追加するには、次の手順を実行し \- ます。

この手順を完了するには、ローカル コンピューター上の **Administrators** または同等のメンバーシップが最低限必要です。  適切なアカウントおよびグループメンバーシップの使用に関する詳細については、「[ローカルおよびドメインの既定のグループ](https://go.microsoft.com/fwlink/?LinkId=83477) \( http: \/ \/ go.microsoft.com fwlink?」を参照して \/ \/ ください。LinkId \= 83477 \) 。

### <a name="to-add-a-token-signing-certificate"></a>トークン署名証明書を追加するには \-

1.  **スタート** 画面で「**AD FS Management**」と入力し、enter キーを押します。

2.  コンソールツリーで、[サービス] をダブルクリックし、[ \- **証明書**] をクリックします。 

3.  [ **操作** ] ウィンドウで、[ **トークン \- 署名証明書の追加** ] リンクをクリックします。

4.  [ **証明書ファイルの参照** ] ダイアログボックスで、追加する証明書ファイルに移動し、証明書ファイルを選択して [ **開く**] をクリックします。

## <a name="additional-references"></a>その他のリファレンス
[チェックリスト:フェデレーション サーバーのセットアップ](Checklist--Setting-Up-a-Federation-Server.md)

[フェデレーション サーバーの証明書の要件](../design/certificate-requirements-for-federation-servers.md)

