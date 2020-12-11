---
description: '詳細情報: リソースパートナーでのフェデレーションアプリケーション戦略の決定'
ms.assetid: 9eab8c43-a0f2-4d19-a5a4-e1399f0d5f25
title: リソース パートナーでのフェデレーション アプリケーション戦略の決定
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 597d0de2b4bd6380e8cba560d72567c70a5ddc6b
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97042300"
---
# <a name="determine-your-federated-application-strategy-in-the-resource-partner"></a>リソース パートナーでのフェデレーション アプリケーション戦略の決定

リソースパートナー組織での新しい Active Directory フェデレーションサービス (AD FS) AD FS インフラストラクチャの設計の重要な部分 \( \) は、フェデレーションに参加するために使用されるアプリケーションとサービスの完全なセットと、それらのリソースの受信者になるアカウントパートナーを決定することです。 フェデレーション アプリケーションおよびサービスの戦略を設計する前に、以下の質問について調査します。

-   ASP.NET アプリケーションまたは Windows Communication Foundation WCF サービスをフェデレーション用に有効化してデプロイし \( \) ますか?

-   企業ネットワーク上のユーザーが Windows 統合認証を使用してフェデレーション アプリケーションまたはサービスにアクセスする必要がありますか。

-   フェデレーション アプリケーションまたはサービスは境界ネットワークのユーザーによって使用されますか。 使用される場合、Windows 統合認証が必要ですか。

-   フェデレーションアプリケーションをホストするすべての Web サーバーが Windows Server オペレーティングシステムを実行し、IIS をインターネットインフォメーションサービスしている \( \) か。

-   フェデレーション アプリケーションまたはサービスがリソースを提供する対象は誰ですか。

これらの質問に答えることで、堅固な AD FS 設計を計画するのに役立ちます。 また、コスト効果が高くリソース効率に優れたフェデレーション アプリケーションおよびサービスの作成にも役立ちます。 組織にとって最も適切なフェデレーション アプリケーションおよびサービスを設計する方法の詳細については、このガイドの次のトピックを参照してください。

-   [Active Directory ユーザーに要求に対応するアプリケーションとサービスへのアクセスを提供する](Provide-Your-Active-Directory-Users-Access-to-Your-Claims-Aware-Applications-and-Services.md)

-   [Active Directory ユーザーに他の組織のアプリケーションとサービスへのアクセスを提供する](Provide-Your-Active-Directory-Users-Access-to-the-Applications-and-Services-of-Other-Organizations.md)

-   [要求に対応するアプリケーションやサービスへのアクセスを別の組織のユーザーに提供する](Provide-Users-in-Another-Organization-Access-to-Your-Claims-Aware-Applications-and-Services.md)

要求に対応する ASP.NET アプリケーションまたは WCF サービスを作成する方法の詳細について \- は、「 [Windows IDENTITY Foundation SDK](https://go.microsoft.com/fwlink/?LinkId=122266)」を参照してください。

## <a name="see-also"></a>関連項目
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)

