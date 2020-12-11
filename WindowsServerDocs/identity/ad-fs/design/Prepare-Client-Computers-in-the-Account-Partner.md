---
description: 詳細については、「アカウントパートナーでクライアントコンピューターを準備する」を参照してください。
ms.assetid: cea6011d-3753-4b95-aaa5-38d4e97d6e42
title: アカウント パートナー内のクライアント コンピューターを準備する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 27c7e49fa35a47c7cfa60e9495600a1988f8e776
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049450"
---
# <a name="prepare-client-computers-in-the-account-partner"></a>アカウント パートナー内のクライアント コンピューターを準備する

アカウントパートナー組織の管理者が Active Directory フェデレーションサービス (AD FS) AD FS フェデレーションアプリケーションにアクセスできるようにクライアントコンピューターを準備する最も簡単な方法 \( \) はグループポリシーを使用することです。 グループ ポリシーは、フェデレーションに必要な特定の証明書と設定を、フェデレーション アプリケーションへのアクセスに使用されるすべてのクライアント コンピューターにプッシュするための便利な方法を提供します。

クライアントコンピューターが証明書のプロンプトや信頼されたサイト関連のプロンプトを表示せずに、フェデレーションアプリケーションにシームレスにアクセスできるように、最初に各クライアントコンピューターを準備してから、組織内に AD FS 展開することをお勧めします。 グループ ポリシーを使用して、次の操作を自動化することを検討してください。

-   各クライアントコンピューターで、アカウントフェデレーションサーバーを信頼するように Internet Explorer を構成します。

    詳細については、「 [Configure Client Computers to Trust the Account Federation Server](../../ad-fs/deployment/Configure-Client-Computers-to-Trust-the-Account-Federation-Server.md)」を参照してください。

-   \( \) \( 各クライアントコンピューターの信頼されたルートにチェーンする SSL 証明書または同等の証明書 Secure Sockets Layer、適切なアカウントフェデレーションサーバー、リソースフェデレーションサーバー、および Web サーバーをインストールし \) ます。

    詳細については、「グループポリシーを使用した [クライアントコンピューターへの証明書の配布](../../ad-fs/deployment/Distribute-Certificates-to-Client-Computers-by-Using-Group-Policy.md)」を参照してください。


## <a name="see-also"></a>関連項目
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
