---
title: Windows 認証のアーキテクチャ
description: Windows Server のセキュリティ
ms.topic: article
ms.assetid: 07c9d6bb-9b03-407d-89b6-97c7551b256b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: 7f2ad45a12f8542e4af9a77a9dc76a9596df2143
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638713"
---
# <a name="windows-authentication-architecture"></a>Windows 認証のアーキテクチャ

>適用先:Windows Server (半期チャネル)、Windows Server 2016

IT プロフェッショナル向けのこの概要トピックでは、Windows 認証の基本的なアーキテクチャスキームについて説明します。

認証とは、システムがユーザーのログオン情報またはサインイン情報を検証するプロセスです。 ユーザーの名前とパスワードが承認済みリストと比較され、システムが一致を検出すると、そのユーザーのアクセス許可リストで指定されたエクステントへのアクセスが許可されます。

Windows Server オペレーティングシステムでは、拡張可能なアーキテクチャの一部として、Negotiate、Kerberos プロトコル、NTLM、Schannel (secure channel)、Digest など、認証セキュリティサポートプロバイダーの既定のセットが実装されています。 これらのプロバイダーによって使用されるプロトコルにより、ユーザー、コンピューター、およびサービスの認証が可能になり、認証プロセスによって、承認されたユーザーとサービスが安全な方法でリソースにアクセスできるようになります。

Windows Server では、アプリケーションは SSPI を使用してユーザーを認証し、認証のための呼び出しを抽象化します。 そのため、開発者は、特定の認証プロトコルの複雑さを理解したり、アプリケーションに認証プロトコルを構築したりする必要はありません。

Windows Server オペレーティングシステムには、Windows セキュリティモデルを構成する一連のセキュリティコンポーネントが含まれています。 これらのコンポーネントによって、アプリケーションは認証と承認を行わずにリソースにアクセスできなくなります。 以下のセクションでは、認証アーキテクチャの要素について説明します。

### <a name="local-security-authority"></a>ローカル セキュリティ機関
ローカルセキュリティ機関 (LSA) は、ローカルコンピューターに対してユーザーを認証およびサインインする保護されたサブシステムです。 さらに、LSA はコンピューター上のローカルセキュリティのあらゆる側面に関する情報を保持します (これらの側面を総称してローカルセキュリティポリシーと呼びます)。 また、名前とセキュリティ識別子 (Sid) を変換するためのさまざまなサービスも用意されています。

セキュリティサブシステムは、コンピューターシステム上のセキュリティポリシーとアカウントを追跡します。 ドメインコントローラーの場合、これらのポリシーとアカウントは、ドメインコントローラーが配置されているドメインに対して有効なものです。 これらのポリシーとアカウントは Active Directory に格納されます。 LSA サブシステムには、オブジェクトへのアクセスの検証、ユーザー権限の確認、および監査メッセージの生成を行うためのサービスが用意されています。

### <a name="security-support-provider-interface"></a>セキュリティサポートプロバイダインターフェイス
セキュリティサポートプロバイダインターフェイス (SSPI) は、分散アプリケーションプロトコルの認証、メッセージの整合性、メッセージのプライバシー、およびセキュリティのサービス品質のために統合されたセキュリティサービスを取得する API です。

SSPI は、Generic Security Service API (GSSAPI) の実装です。 SSPI は、分散アプリケーションが複数のセキュリティプロバイダーのいずれかを呼び出して、セキュリティプロトコルの詳細情報を知らずに認証済み接続を取得できるメカニズムを提供します。

## <a name="additional-references"></a>その他の参照情報

-   [セキュリティ サポート プロバイダー インターフェイスのアーキテクチャ](security-support-provider-interface-architecture.md)

-   [Windows 認証での資格情報の処理](credentials-processes-in-windows-authentication.md)

-   [Windows 認証の技術概要](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dn169029(v=ws.10))