---
title: リモート RADIUS サーバー グループ
description: このトピックでは、Windows Server 2016 のネットワークポリシーサーバーのリモート RADIUS サーバーグループの概要について説明します。
manager: brianlic
ms.topic: article
ms.assetid: d81678a7-be21-48f2-9b3f-5a75d6aef013
ms.author: lizross
author: eross-msft
ms.openlocfilehash: 36c1f50b840404c16c67a6252826f76ef5e2b5ec
ms.sourcegitcommit: dfa48f77b751dbc34409aced628eb2f17c912f08
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2020
ms.locfileid: "87969369"
---
# <a name="remote-radius-server-groups"></a>リモート RADIUS サーバー グループ

>適用先:Windows Server (半期チャネル)、Windows Server 2016

ネットワークポリシーサーバー (NPS) をリモート認証ダイヤルインユーザーサービス (RADIUS) プロキシとして構成する場合、NPS を使用して、接続要求を処理できる RADIUS サーバーに接続要求を転送します。これは、ユーザーまたはコンピューターのアカウントが置かれているドメインで認証と承認を実行できるためです。 たとえば、信頼されていないドメインにある 1 つ以上の RADIUS サーバーに接続要求を転送する場合、NPS を RADIUS プロキシとして構成して、信頼されていないドメインにあるリモート RADIUS サーバーに要求を転送できます。

>[!NOTE]
>リモート RADIUS サーバーグループは、Windows グループとは関係ありません。

NPS を RADIUS プロキシとして構成するには、接続要求ポリシーを作成して、NPS がどのメッセージを転送し、どこに送信するかを評価するために必要なすべての情報をそのポリシーに含める必要があります。

NPS にリモート RADIUS サーバー グループを構成して、そのグループに接続要求ポリシーを構成することは、NPS が接続要求を転送する場所を設計することです。

## <a name="configuring-radius-servers-for-a-group"></a>グループに RADIUS サーバーを構成する

リモート RADIUS サーバー グループは、1 つ以上の RADIUS サーバーを含む、名前の付けられたグループです。 複数のサーバーを構成する場合、負荷分散の設定を行って、プロキシがサーバーを使用する順番を指定するか、またはグループ内のすべてのサーバーに RADIUS メッセージのフローを分散することにより、1 つまたはいくつかのサーバーに多数の接続要求が集まり、過負荷になることがないようにします。

グループ内の各サーバーには、次の設定があります。

- **名前またはアドレス**。 グループの各メンバーには、グループ内で一意の名前を付ける必要があります。 名前には IP アドレスを使用するか、IP アドレスに解決できる名前を付けます。

- **認証とアカウンティング**。 認証要求、アカウンティング要求、またはその両方を、各リモート RADIUS サーバーグループメンバーに転送できます。

- **負荷分散**。 優先順位を設定して、グループ内のどのメンバーをプライマリ サーバー (優先順位を 1 に設定) にするかを指定します。 同じ優先順位のグループ メンバーについては、それぞれのサーバーに RADIUS メッセージが送られる頻度を、重みの設定を使用して計算します。 追加の設定を使用して、グループメンバーが最初に使用できなくなったときに NPS が検出する方法と、使用できないと判断された後に使用可能になるタイミングを構成できます。

リモート RADIUS サーバーグループを構成した後、接続要求ポリシーの [認証] および [アカウンティング] 設定でグループを指定できます。 したがって、リモート RADIUS サーバー グループは最初に構成できます。 次に、新しく構成されたリモート RADIUS サーバー グループを使用するための接続要求ポリシーを構成できます。 または、接続要求ポリシーを作成するときに、新しい接続要求ポリシー ウィザードを使用して新しいリモート RADIUS サーバー グループを作成できます。

NPS の詳細については、「[ネットワークポリシーサーバー (nps)](nps-top.md)」を参照してください。
