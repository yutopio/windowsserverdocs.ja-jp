---
description: 詳細については、「フェデレーションサーバーファームのサービスアカウントを手動で構成する」を参照してください。
ms.assetid: 5a1ae56b-adcb-447e-9e34-c0629d7cb241
title: フェデレーション サーバー ファームのサービス アカウントを手動で構成する
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: afedde422f0a46975fcbb61912773a992c688309
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97043330"
---
# <a name="manually-configure-a-service-account-for-a-federation-server-farm"></a>フェデレーション サーバー ファームのサービス アカウントを手動で構成する

Active Directory フェデレーションサービス (AD FS) AD FS でフェデレーションサーバーファーム環境を構成する場合は \( 、 \) \( ファームが配置される Active Directory Domain Services AD DS で専用のサービスアカウントを作成し、構成する必要があり \) ます。 次に、このアカウントを使用するために、ファーム内の各フェデレーション サーバーを構成します。 企業ネットワーク上のクライアントコンピューターが Windows 統合認証を使用して AD FS ファーム内のいずれかのフェデレーションサーバーに対して認証を行うことができるようにするには、組織で次のタスクを完了する必要があります。

> [!IMPORTANT]
> AD FS 3.0 (Windows Server 2012 R2) の場合、AD FS は、グループの管理された [サービスアカウント](../../../security/group-managed-service-accounts/group-managed-service-accounts-overview.md) \( gMSA をサービスアカウントとして使用することをサポートしてい \) ます。  これは、時間の経過と共にサービスアカウントのパスワードを管理する必要がないため、推奨されるオプションです。  このドキュメントでは、Windows Server 2008 R2 以前のドメイン機能レベル dfl をまだ実行しているドメインなど、従来のサービスアカウントを使用する別のケースについて説明し \( \) ます。

> [!NOTE]
> この手順のタスクは、フェデレーション サーバー ファーム全体で 1 回のみ実行する必要があります。 後になって、AD FS フェデレーション サーバーの構成ウィザードを使ってフェデレーション サーバーを作成する場合、ファーム内のフェデレーション サーバーごとに、**[サービス アカウント]** ウィザード ページでこれと同じアカウントを指定する必要があります。

#### <a name="create-a-dedicated-service-account"></a>専用のサービス アカウントを作成する

1.  \/Id プロバイダー組織に配置されている Active Directory フォレストに専用のユーザーサービスアカウントを作成します。 このアカウントは、ファームシナリオで Kerberos 認証プロトコルが動作し、 \- 各フェデレーションサーバーでパススルー認証を許可するために必要です。 このアカウントは、フェデレーションサーバーファームの目的でのみ使用してください。

2.  ユーザー アカウントのプロパティを編集し、[**パスワードを無期限にする**] チェック ボックスをオンにします。 この操作によって、ドメイン パスワードの変更要件によってサービス アカウントの機能が中断されることはなくなります。

    > [!NOTE]
    > この専用アカウントの Network Service アカウントを使用する場合、Windows 統合認証経由でアクセスを試みると、ランダムに失敗する結果となります。これは、Kerberos チケットがサーバー間で検証されないことが原因です。

#### <a name="to-set-the-spn-of-the-service-account"></a>サービス アカウントの SPN を設定するには

1.  AD FS AppPool のアプリケーションプール id はドメインユーザーのサービスアカウントとして実行されているため \/ 、 \( \) Setspn.exe コマンドラインツールを使用して、ドメイン内のそのアカウントのサービスプリンシパル名の SPN を構成する必要があり \- ます。 Setspn.exe は、Windows Server 2008 を実行しているコンピューターに既定でインストールされます。 ユーザーサービスアカウントが存在する同じドメインに参加しているコンピューターで、次のコマンドを実行し \/ ます。

    ```
    setspn -a host/<server name> <service account>
    ```

    たとえば、すべてのフェデレーションサーバーがドメインネームシステム DNS ホスト名 fs.fabrikam.com の下にクラスター化され \( \) ており、AD FS AppPool に割り当てられているサービスアカウント名が adfs2farm である場合、コマンドを次のように入力し、enter キーを押します。

    ```
    setspn -a host/fs.fabrikam.com adfs2farm
    ```

    このタスクはこのアカウントについて 1 回だけ実行する必要があります。

2.  AD FS AppPool id がサービスアカウントに変更された後、SQL Server データベースのアクセス制御リストの acl を設定して、 \( \) この新しいアカウントへの読み取りアクセスを許可し、AD FS AppPool がポリシーデータを読み取ることができるようにします。

