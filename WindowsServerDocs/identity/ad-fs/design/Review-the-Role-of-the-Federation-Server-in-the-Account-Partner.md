---
description: 詳細については、アカウントパートナーのフェデレーションサーバーの役割の確認に関するページを参照してください。
ms.assetid: d0ba3c0d-869f-4e24-89d7-499da7576f22
title: アカウント パートナー内のフェデレーション サーバーの役割を確認する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: ccde30456f09d2bb86053db457db5758fd03185b
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049400"
---
# <a name="review-the-role-of-the-federation-server-in-the-account-partner"></a>アカウント パートナー内のフェデレーション サーバーの役割を確認する

Active Directory フェデレーションサービス (AD FS) AD FS のフェデレーションサーバーは、 \( \) セキュリティトークンの発行者として機能します。 フェデレーションサーバーは、ローカル属性ストアに存在するアカウント値に基づいて要求を生成し、セキュリティトークンにパッケージ化します。これにより、ユーザーは \- \- \( \- \( \) \) 、リソースパートナー組織でホストされているシングルサインオン SSO を使用して、Web ブラウザーベースのアプリケーションにシームレスにアクセスできるようになります。

> [!NOTE]
> ユーザーが Web ブラウザーを使用してフェデレーションアプリケーションにアクセスすると、フェデレーションサーバーは、その Web ブラウザーベースのアプリケーションのログオン状態を維持するために、ユーザーに自動的に cookie を発行し \- \- ます。 これらのクッキーには、ユーザーの信頼性情報が含まれます。 Cookie によって SSO 機能が有効になり、ユーザーは \- リソースパートナー内のさまざまな Web ブラウザーベースのアプリケーションにアクセスするたびに資格情報を入力する必要がなくなり \- ます。

Web SSO の設計では、境界ネットワークを使用する組織は、インターネットユーザーがアプリケーションにアクセスできるようにするには、境界ネットワークにフェデレーションサーバープロキシをインストールする必要があります。 フェデレーション Web SSO 設計では、アカウントパートナー組織の企業ネットワークに少なくとも1つのフェデレーションサーバーがインストールされ、リソースパートナー組織の企業ネットワークに少なくとも1つのフェデレーションサーバーがインストールされている必要があります。

> [!NOTE]
> アカウントパートナー組織でフェデレーションサーバーコンピューターをセットアップする前に、まず、そのコンピューターを Active Directory フォレスト内の任意のドメインに参加させる必要があります。このフォレストでフェデレーションサーバーを使用して、そのフォレストからユーザーを認証します。 詳細については、「 [Checklist: Setting Up a Federation Server](../../ad-fs/deployment/Checklist--Setting-Up-a-Federation-Server.md)」を参照してください。

## <a name="see-also"></a>関連項目
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
