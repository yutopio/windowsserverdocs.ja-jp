---
description: 詳細については、Active Directory ユーザーに要求に対応するアプリケーションとサービスへのアクセスを提供する」を参照してください。
ms.assetid: d254fca3-85a1-424d-ac22-d6687ec3798e
title: Active Directory ユーザーに要求に対応するアプリケーションとサービスへのアクセスを提供する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: a37147b46dc0ed8a6aac7700ad3549052c90c4bb
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049420"
---
# <a name="provide-your-active-directory-users-access-to-your-claims-aware-applications-and-services"></a>Active Directory ユーザーに要求に対応するアプリケーションとサービスへのアクセスを提供する

Active の Directory フェデレーション サービスのアカウント パートナー組織の管理者であると \(AD FS\) 展開して、1 つを提供する展開の目的をいる\-記号\-に \(SSO\) 人の従業員が会社のネットワークにホストされているリソースへのアクセス。

-   企業ネットワークの Active Directory フォレストにログオンした従業員は、SSO を使用して、管理者の組織内の境界ネットワークの複数のアプリケーションやサービスにアクセスできます。 これらのアプリケーションとサービスは、AD FS によってセキュリティで保護されています。

    Fabrikam が企業ネットワーク上の社員へのフェデレーション Web へのアクセスにするなど、\-ベースのアプリケーションの Fabrikam の境界ネットワークでホストされています。

-   Active Directory ドメインにログオンしているリモートの社員は、AD FS にフェデレーション アクセスするために、組織内のフェデレーション サーバーから AD FS トークンを取得できます\-Web をセキュリティで保護された\-ベースのアプリケーションまたはも、組織内にあるサービスです。

-   Active Directory 属性ストアの情報を、従業員の AD FS トークンに設定できます。

このような展開目標を達成するには、次のコンポーネントが必要です。

-   **Active Directory Domain Services \(AD DS \) :** AD DS には、AD FS トークンの生成に使用される従業員のユーザーアカウントが含まれています。 グループのメンバーシップや属性などの情報は、グループ要求およびカスタム要求として AD FS トークンに設定されます。

    > [!NOTE]
    > ライトウェイト ディレクトリ アクセス プロトコルを使用することもできます。 \(LDAP\) または構造化照会言語 \(SQL\) を格納するには、AD FS トークンを生成します。

-   **会社の DNS:** ドメイン ネーム システムのこの実装 \(DNS\) シンプルなホストを含む \(A\) リソース レコードのイントラネット クライアントは、アカウント フェデレーション サーバーを検出できるようにします。 DNS のこの実装では、企業ネットワークで必要とされる他の DNS レコードもホストされる可能性があります。 詳細については、「[フェデレーション サーバーの名前解決の要件](Name-Resolution-Requirements-for-Federation-Servers.md)」をご覧ください。

-   **アカウント パートナーのフェデレーション サーバー:** このフェデレーション サーバーが、アカウント パートナー フォレスト内のドメインに参加しています。 従業員のユーザー アカウントを認証し、AD FS トークンを生成します。 従業員のクライアント コンピューターは、AD FS トークンを生成するには、このフェデレーション サーバーに対して Windows 統合認証を実行します。 詳細については、「 [Review the Role of the Federation Server in the Account Partner](Review-the-Role-of-the-Federation-Server-in-the-Account-Partner.md)」を参照してください。

    アカウント パートナーのフェデレーション サーバーは、次のユーザーを認証できます。

    -   このドメインにユーザー アカウントを持つ従業員

    -   このフォレスト内のどこかにユーザー アカウントを持つ従業員

    -   このフォレストによって信頼されているフォレスト内の任意の場所にあるユーザーアカウントを持つ従業員 (双 \( \- 方向の Windows 信頼)\)

-   **従業員:** 従業員は、 \- \( \) \- \( 企業ネットワークにログオンしている間、サポートされている web ブラウザーを介して、アプリケーションまたは web ベースのアプリケーションを介して web ベースのサービスにアクセス \) します。 企業ネットワーク上の従業員のクライアント コンピューターは、認証用のフェデレーション サーバーと直接通信します。

リンク先のトピックの情報を確認した後は、「 [Checklist: Implementing a Federated Web SSO Design](../../ad-fs/deployment/Checklist--Implementing-a-Federated-Web-SSO-Design.md)」の手順に従って、この目標のデプロイを開始できます。

次の図は、この AD FS 展開の目的に必要なコンポーネントの各を示します。

![要求へのアクセスします。](media/31394ea8-fecb-4372-ac3f-cc3cf566ffc9.gif)

## <a name="see-also"></a>関連項目
[Windows Server 2012 での AD FS 設計ガイド](AD-FS-Design-Guide-in-Windows-Server-2012.md)
