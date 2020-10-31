---
ms.assetid: cc2834ec-8f66-4209-aba3-402d710cd1bd
title: ドメイン コントローラーの場所
author: iainfoulds
ms.author: daveba
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: d22abba814d9cd4b18294b3c54d550b28c2dfef5
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93068724"
---
# <a name="domain-controller-location"></a>ドメイン コントローラーの場所

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

クライアントはドメインネームシステム (DNS) を使用してドメインコントローラーを特定し、ログオン要求の処理や、発行されたリソースのディレクトリの検索などの操作を完了します。 ドメインコントローラーは、クライアントや他のコンピューターが検出できるように、さまざまなレコードを DNS に登録します。 これらのレコードは、まとめてロケーターレコードと呼ばれます。

また、ドメインコントローラーは、他のドメインコントローラーを検索したり、レプリケーションなどのタスクを実行したりするためにも DNS を使用します。 ドメインコントローラーが他のドメインコントローラーを検索するプロセスは、クライアントがドメインコントローラーを特定するプロセスと同じです。



