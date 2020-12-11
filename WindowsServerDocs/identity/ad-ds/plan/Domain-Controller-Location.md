---
description: 詳細については、「ドメインコントローラーの場所」を参照してください。
ms.assetid: cc2834ec-8f66-4209-aba3-402d710cd1bd
title: ドメイン コントローラーの場所
author: iainfoulds
ms.author: daveba
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 6885f9cabc9f9f60939e41858f04537cb1bcfcbe
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97045120"
---
# <a name="domain-controller-location"></a>ドメイン コントローラーの場所

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

クライアントはドメインネームシステム (DNS) を使用してドメインコントローラーを特定し、ログオン要求の処理や、発行されたリソースのディレクトリの検索などの操作を完了します。 ドメインコントローラーは、クライアントや他のコンピューターが検出できるように、さまざまなレコードを DNS に登録します。 これらのレコードは、まとめてロケーターレコードと呼ばれます。

また、ドメインコントローラーは、他のドメインコントローラーを検索したり、レプリケーションなどのタスクを実行したりするためにも DNS を使用します。 ドメインコントローラーが他のドメインコントローラーを検索するプロセスは、クライアントがドメインコントローラーを特定するプロセスと同じです。



