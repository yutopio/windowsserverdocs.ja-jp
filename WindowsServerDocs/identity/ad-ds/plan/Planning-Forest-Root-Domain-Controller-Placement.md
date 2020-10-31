---
ms.assetid: 2a2f493a-9796-454a-9721-e223b799dfa7
title: フォレスト ルート ドメイン コントローラーの配置を計画する
author: iainfoulds
ms.author: daveba
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: ab34eb19c880fbe22b9da74a6745d9277a564cb4
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93071064"
---
# <a name="planning-forest-root-domain-controller-placement"></a>フォレスト ルート ドメイン コントローラーの配置を計画する

> 適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

フォレストルートドメインコントローラーは、自身以外のドメインのリソースにアクセスする必要があるクライアントの信頼パスを作成するために必要です。 ハブの場所およびデータセンターをホストする場所に、フォレストルートドメインコントローラーを配置します。 特定の場所のユーザーが同じ場所にある他のドメインのリソースにアクセスする必要があり、データセンターとユーザーの場所の間のネットワークの可用性が低い場合は、その場所にフォレストルートドメインコントローラーを追加するか、2つのドメイン間にショートカットの信頼を作成することができます。 フォレストルートドメインコントローラーをその場所に配置する他の理由がない限り、ドメイン間にショートカットの信頼を作成する方がコスト効率が高くなります。

ショートカットの信頼は、いずれかのドメインにあるユーザーからの認証要求を最適化するのに役立ちます。 ドメイン間のショートカットの信頼の詳細については、「 [ショートカットの信頼を作成する場合](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc754538(v=ws.11))」を参照してください。

フォレストルートドメインコントローラーの配置を文書化するのに役立つワークシートについては、「 [Windows Server 2003 展開キット用のジョブエイド](https://microsoft.com/download/details.aspx?id=9608)」、「Job_Aids_Designing_and_Deploying_Directory_and_Security_Services.zip をダウンロードする」、および「ドメインコントローラーの配置」 (DSSTOPO_4.doc) を参照してください。

この情報は、フォレストのルートドメインを作成するときに参照する必要があります。 フォレストルートドメインの展開の詳細については、「 [Windows Server 2008 のフォレストルートドメインの展開](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174(v=ws.10))」を参照してください。
