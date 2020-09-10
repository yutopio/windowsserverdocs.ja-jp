---
title: TLS/SSL の概要 (Schannel SSP)
description: Windows Server のセキュリティ
ms.topic: article
ms.assetid: 1b7b0432-1bef-4912-8c9a-8989d47a4da9
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 05/16/2018
ms.openlocfilehash: 21ad7977039eda311dd6f093fc53c09c08cf0317
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637843"
---
# <a name="tlsssl-overview-schannel-ssp"></a>TLS/SSL の概要 (Schannel SSP)

>適用先:Windows Server (半期チャネル)、Windows Server 2016、Windows 10

IT 担当者向けのこのトピックでは、Schannel セキュリティサービスプロバイダー (SSP) を使用した Windows での TLS と SSL の実装について説明します。これは、実際のアプリケーション、Microsoft の実装の変更点、およびソフトウェアの要件に加え、Windows Server 2012 および Windows 8 に関するその他のリソースについて説明します。

## <a name="description"></a><a name="BKMK_OVER"></a>説明
Schannel は、インターネットで標準的に用いられている 2 種類の認証プロトコル、Secure Sockets Layer (SSL) とトランスポート層セキュリティ (TLS) を実装するセキュリティ サポート プロバイダー (SSP) です。

セキュリティ サポート プロバイダー インターフェイス (SSPI) は、認証など、セキュリティ関係の機能を実行するために Windows システムで用いられる API の 1 種です。 SSPI は、Schannel SSP を含む複数の Ssp に共通のインターフェイスとして機能します。

TLS バージョン1.0、1.1、1.2、SSL バージョン2.0 および3.0、データグラムトランスポート層セキュリティ \( DTLS \) プロトコルバージョン1.0、プライベート通信トランスポートの \( PCT \) プロトコルは、公開キーの暗号化に基づいています。 Schannel 認証プロトコル スイートは、これらのプロトコルを備えています。 どの Schannel プロトコルでも、クライアント/サーバー モデルが使用されています。

## <a name="applications"></a><a name="BKMK_APP"></a>アプリケーション
ネットワークを管理するうえでの課題の 1 つが、信頼されていないネットワークを介してアプリケーション間で送信されるデータを保護することです。 TLS と SSL を使用してサーバーとクライアントコンピューターを認証し、そのプロトコルを使用して認証されたパーティ間のメッセージを暗号化することができます。

たとえば、TLS/SSL を使うと次のようなことができます。

-   E コマース Web サイトとのトランザクションの SSL による保護
-   SSL で保護された Web サイトにアクセスするクライアントの認証
-   リモート アクセス
-   SQL アクセス
-   電子メール

## <a name="requirements"></a><a name="BKMK_SOFT"></a>必要条件
TLS および SSL プロトコルは、クライアント/サーバーモデルを使用し、公開キー基盤を必要とする証明書認証に基づいています。

## <a name="server-manager-information"></a><a name="BKMK_INSTALL"></a>サーバー マネージャー情報
TLS、SSL、または Schannel を実装するために必要な構成手順はありません。

## <a name="additional-references"></a>その他の参照情報 ##

-   [Schannel セキュリティ パッケージ](/windows/desktop/com/schannel)
-   [セキュリティで保護されたチャネル](/windows/desktop/SecAuthN/secure-channel)
-   [トランスポート層セキュリティプロトコル](/windows/desktop/SecAuthN/transport-layer-security-protocol)