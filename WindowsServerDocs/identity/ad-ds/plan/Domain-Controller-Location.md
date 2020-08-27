---
ms.assetid: cc2834ec-8f66-4209-aba3-402d710cd1bd
title: ドメイン コントローラーの場所
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: ada91f7205ba12e4d37a02e3503647c9560ccdd8
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/26/2020
ms.locfileid: "88939272"
---
# <a name="domain-controller-location"></a>ドメイン コントローラーの場所

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

クライアントはドメインネームシステム (DNS) を使用してドメインコントローラーを特定し、ログオン要求の処理や、発行されたリソースのディレクトリの検索などの操作を完了します。 ドメインコントローラーは、クライアントや他のコンピューターが検出できるように、さまざまなレコードを DNS に登録します。 これらのレコードは、まとめてロケーターレコードと呼ばれます。

また、ドメインコントローラーは、他のドメインコントローラーを検索したり、レプリケーションなどのタスクを実行したりするためにも DNS を使用します。 ドメインコントローラーが他のドメインコントローラーを検索するプロセスは、クライアントがドメインコントローラーを特定するプロセスと同じです。



