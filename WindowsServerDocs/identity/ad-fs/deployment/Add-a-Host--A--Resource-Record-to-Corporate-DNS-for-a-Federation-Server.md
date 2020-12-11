---
description: 詳細については、「フェデレーションサーバーの企業 DNS にホスト (A) リソースレコードを追加する」を参照してください。
ms.assetid: 026747c7-4c34-41c7-b7ea-27f9a7f64a35
title: 企業 DNS にフェデレーション サーバーのホスト (A) リソース レコードを追加する
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 00e2366de66eced2ad0cbe3a731f5f6afceb18f6
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97047920"
---
# <a name="add-a-host-a-resource-record-to-corporate-dns-for-a-federation-server"></a>企業 DNS にフェデレーション サーバーのホスト (A) リソース レコードを追加する



企業ネットワーク上のクライアントが Windows 統合認証を使用してフェデレーションサーバーに正常にアクセスできるようにするには、 \( \) まず、アカウントフェデレーションサーバーのホスト名を解決する企業ドメインネームシステム DNS で、ホスト a リソースレコードを作成する必要があり \( \) \( ます。たとえば、fs.fabrikam.com \) はフェデレーションサーバーまたはフェデレーションサーバークラスターの IP アドレスになります。 次の手順を使用して、ホスト a \( \) リソースレコードをフェデレーションサーバーの企業 DNS に追加できます。

**Administrators**、またはそれと同等のメンバーシップが、この手順を実行するために最低限必要なメンバーシップです。  適切なアカウントおよびグループメンバーシップの使用方法の詳細については、「 [ローカルおよびドメインの既定のグループ](https://go.microsoft.com/fwlink/?LinkId=83477)」を参照してください。

### <a name="to-add-a-host-a-resource-record-to-corporate-dns-for-a-federation-server"></a>ホスト a \( \) リソースレコードをフェデレーションサーバーの企業 DNS に追加するには

1.  企業ネットワークの DNS サーバーで、DNS スナップインを開き \- ます。

2.  コンソールツリーで、 \- 該当する前方参照ゾーンを右クリックし、[**新しいホスト \( A または AAAA \)**] をクリックします。

3.  [ **名前**] に、フェデレーションサーバーまたはフェデレーションサーバークラスターのコンピューター名のみを入力します。たとえば、完全修飾ドメイン名 FQDN fs.fabrikam.com の場合は、 \( \) 「 **fs**」と入力します。

4.  [ **Ip アドレス**] に、フェデレーションサーバーまたはフェデレーションサーバークラスターの ip アドレス (たとえば、192.168.1.4) を入力します。

5.  **[ホストの追加]** をクリックします。

## <a name="additional-references"></a>その他のリファレンス
[チェックリスト:フェデレーション サーバーのセットアップ](Checklist--Setting-Up-a-Federation-Server.md)

[フェデレーション サーバーの名前解決の要件](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807055(v=ws.11))

