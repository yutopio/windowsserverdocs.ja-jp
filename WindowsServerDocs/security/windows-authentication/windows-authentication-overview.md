---
title: Windows 認証の概要
description: Windows Server のセキュリティ
ms.topic: article
ms.assetid: 485a0774-0785-457f-a964-0e9403c12bb1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: 4a2b5e6b48a56a1a2148df262d2785640ac6054d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638696"
---
# <a name="windows-authentication-overview"></a>Windows 認証の概要

>適用先:Windows Server (半期チャネル)、Windows Server 2016

IT 担当者向けのこのナビゲーション トピックでは、Windows 認証およびログオン テクノロジに関するドキュメント リソースを示します。これには、製品評価、ファースト ステップ ガイド、手順、設計と展開のガイド、テクニカル リファレンス、コマンド リファレンスなどが含まれます。

## <a name="feature-description"></a>機能の説明
認証は、オブジェクト、サービス、または利用者の ID を検証するプロセスです。 オブジェクトを認証する目的は、そのオブジェクトが本物であることを確認することにあります。 サービスまたは利用者を認証する目的は、提示された資格情報が本物であることを確認することにあります。

ネットワーキングのコンテキストでの認証とは、ネットワーク アプリケーションまたはリソースに身元を証明する行為を表します。 通常、id は、公開キーの暗号化または共有キーと同様に、ユーザーが知っているキーのみを使用する暗号化操作によって証明されます。 認証交換のサーバー側は、署名されたデータを既知の暗号化キーと比較して、認証試行を検証します。

暗号化キーを安全な一元的な場所に保管すると、認証プロセスのスケーラビリティと保守性が向上します。 Active Directory Domain Services は、 \( ユーザーの資格情報である暗号化キーを含む id 情報を格納するための推奨されるテクノロジであり、既定のテクノロジです \) 。 既定の NTLM および Kerberos 実装には、Active Directory が必要です。

認証手法は、単純なログオンから、ユーザーがパスワードを知っているかに基づいてユーザーを識別し、ユーザーが持つトークン、公開キー証明書、生体認証を使用するより強力なセキュリティメカニズムに限定します。 ビジネス環境のサービスまたはユーザーは、1 つまたは複数の場所に配置された複数の種類のサーバー上の複数のアプリケーションやリソースにアクセスすることがあります。 これらの理由から、認証では、他のプラットフォームや他の Windows オペレーティング システムの環境をサポートする必要があります。

Windows オペレーティングシステムでは、 \/ \( \/ \) 拡張可能なアーキテクチャの一部として、Kerberos、NTLM、トランスポート層セキュリティ Secure Sockets Layer TLS SSL、ダイジェストなどの認証プロトコルの既定のセットが実装されています。 加えて、いくつかのプロトコルは、Negotiate、Credential Security Support Provider などの認証パッケージに統合されています。 これらのプロトコルやパッケージによって、ユーザー、コンピューター、サービスの認証が可能になります。また、認証処理によって、承認されたユーザーとサービスが安全な方法でリソースにアクセスできるようになります。

Windows 認証の詳細には、次の内容も含まれます。

-   [Windows 認証の概念](windows-authentication-concepts.md)

-   [Windows ログオンのシナリオ](windows-logon-scenarios.md)

-   [Windows 認証のアーキテクチャ](windows-authentication-architecture.md)

-   [セキュリティ サポート プロバイダー インターフェイスのアーキテクチャ](security-support-provider-interface-architecture.md)

-   [Windows 認証での資格情報の処理](credentials-processes-in-windows-authentication.md)

-   [Windows 認証で使用されるグループ ポリシー設定](group-policy-settings-used-in-windows-authentication.md)

「 [Windows 認証の技術概要](windows-authentication-technical-overview.md)」を参照してください。

## <a name="practical-applications"></a>実際の適用例
Windows 認証は、情報が信頼できるソース (人や別のコンピューターなどのコンピューター オブジェクト) から送信されていることを確認するために使用します。 Windows には、この操作を行うためのさまざまな方法が用意されています。次の表に、これらの方法について説明します。

|宛先...|特徴量|説明|
|----|------|--------|
|Active Directory ドメイン内の認証|Kerberos|Microsoft Windows &nbsp; Server オペレーティングシステムには、公開キー認証用の Kerberos version 5 認証プロトコルと拡張機能が実装されています。 Kerberos 認証クライアントはセキュリティサポートプロバイダー SSP として実装され、 \( \) セキュリティサポートプロバイダーインターフェイス SSPI を使用してアクセスでき \( \) ます。 初期のユーザー認証は、Winlogon シングルサインオンアーキテクチャと統合されてい \- ます。 Kerberos キー配布センター \( KDC \) は、ドメインコントローラーで実行されている他の Windows Server セキュリティサービスと統合されています。 KDC は、そのセキュリティアカウントデータベースとしてドメインの Active Directory Directory サービスデータベースを使用します。 既定の Kerberos 実装には、Active Directory が必要です。<p>その他のリソースについては、「[Kerberos 認証の概要](../kerberos/kerberos-authentication-overview.md)」を参照してください。|
|Web 上のセキュリティで保護された認証|\/Schannel セキュリティサポートプロバイダーに実装されている TLS SSL|トランスポート層セキュリティ \( TLS \) プロトコルバージョン1.0、1.1、1.2、Secure Sockets Layer \( SSL \) プロトコル、バージョン2.0 と3.0、データグラムトランスポート層セキュリティプロトコルバージョン1.0、およびプライベート通信トランスポートの \( PCT \) プロトコルのバージョン1.0 は、公開キーの暗号化に基づいています。 セキュリティで保護されたチャネル \( Schannel \) プロバイダー認証プロトコルスイートは、これらのプロトコルを提供します。 すべての Schannel プロトコルでは、クライアント/サーバー モデルが使用されています。<p>その他のリソースについては、「 [TLS-SSL &#40;SCHANNEL SSP&#41; の概要](../tls/tls-ssl-schannel-ssp-overview.md)」を参照してください。|
|Web サービスまたはアプリケーションの認証|統合 Windows 認証<p>ダイジェスト認証|その他のリソースについては、「[Integrated Windows Authentication (統合 Windows 認証)](/previous-versions/windows/it-pro/windows-server-2003/cc758557(v=ws.10))」、「[Digest Authentication (ダイジェスト認証)](/previous-versions/windows/it-pro/windows-server-2003/cc738318(v=ws.10))」、および「[Advanced Digest Authentication (高度なダイジェスト認証)](/previous-versions/windows/it-pro/windows-server-2003/cc783131(v=ws.10))」を参照してください。|
|レガシ アプリケーションの認証|NTLM|NTLM はチャレンジ \- 応答スタイルの認証プロトコルです。NTLM プロトコルは、認証に加えて、必要に応じて、NTLM の署名機能と封印機能によって、セッションセキュリティ (特にメッセージの整合性と機密性) を提供します。<p>その他のリソースについては、「[NTLM の概要](../kerberos/ntlm-overview.md)」を参照してください。|
|多要素認証の利用|スマート カードのサポート<p>生体認証のサポート|スマートカードは、 \- クライアント認証、ドメインへのログオン、コード署名、電子メールのセキュリティ保護などのタスクにセキュリティソリューションを提供するための、改ざんされにくく、ポータブルな方法です \- 。<p>生体認証は、一人一人異なる不変の身体的特徴を測定することによって個人を特定します。 生体認証に最も多く使われている身体的特徴の 1 つは指紋です。指紋を使って生体認証を行う数え切れないほどのデバイスが、パーソナル コンピューターや周辺機器に組み込まれています。<p>その他のリソースについては、「 [スマートカードのテクニカルリファレンス](/windows/security/identity-protection/smart-cards/smart-card-windows-smart-card-technical-reference)」を参照してください。 |
|資格情報のローカル管理、保管、再利用|資格情報の管理<p>ローカル セキュリティ機関<p>パスワード|Windows の資格情報管理を使うと、資格情報を安全に保管できます。 資格情報は、 \( \) リソースにアクセスするたびに正しい資格情報が提示されるように、アプリまたは web サイトを介して、セキュリティで保護されたデスクトップで収集されます。<p>
|最新の認証保護によるレガシ システムの強化|認証の拡張保護 (Extended Protection for Authentication)|この機能は、統合 Windows 認証 iwa を使用してネットワーク接続を認証するときに、資格情報の保護と処理を強化し \( \) ます。|

## <a name="software-requirements"></a>ソフトウェア要件
Windows 認証は、Windows オペレーティング システムの以前のバージョンとの互換性があるように設計されています。 ただし、各リリースでの改良が必ずしも以前のバージョンに適用されるとは限りません。 詳細については、特定の機能のドキュメントを参照してください。

## <a name="server-manager-information"></a>サーバー マネージャー情報
グループ ポリシーを使用して、多くの認証機能を構成できます。グループ ポリシーは、サーバー マネージャーを使用してインストールできます。 Windows 生体認証フレームワーク機能をインストールするには、サーバー マネージャーを使用します。 Web サーバー IIS や Active Directory Domain Services などの認証方法に依存するその他のサーバーの役割は、 \( \) サーバーマネージャーを使用してインストールすることもできます。

## <a name="related-resources"></a>関連リソース

|認証テクノロジ|リソース|
|----------------|-------|
|Windows 認証|[Windows 認証の技術概要](../windows-authentication/windows-authentication-technical-overview.md)<br />バージョン間の違い、一般的な認証の概念、ログオンのシナリオ、サポートされるバージョンのアーキテクチャ、適用可能な設定などのトピックが含まれます。|
|Kerberos|[Kerberos Authentication Overview](../kerberos/kerberos-authentication-overview.md)<p>[Kerberos の制約付き委任の概要](../kerberos/kerberos-constrained-delegation-overview.md)<p>[Kerberos 認証のテクニカルリファレンス](/previous-versions/windows/it-pro/windows-server-2003/cc739058(v=ws.10)) \(2003\)<p>[Kerberos フォーラム](/answers/topics/windows-server-security.html)|
|TLS \/ SSL および DTLS \( Schannel セキュリティサポートプロバイダー\)|[TLS-SSL &#40;Schannel SSP&#41; の概要](../tls/tls-ssl-schannel-ssp-overview.md)<p>[Schannel セキュリティ サポート プロバイダーのテクニカル リファレンス](../tls/schannel-security-support-provider-technical-reference.md)|
|ダイジェスト認証|[ダイジェスト認証のテクニカルリファレンス](/previous-versions/windows/it-pro/windows-server-2003/cc782794(v=ws.10)) \(2003\)|
|NTLM|[NTLM Overview](../kerberos/ntlm-overview.md)<br />現在および過去のリソースへのリンクが含まれます|
|PKU2U|[Windows の PKU2U の概要](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd560634(v=ws.10))|
|スマート カード|[スマートカードのテクニカルリファレンス](/windows/security/identity-protection/smart-cards/smart-card-windows-smart-card-technical-reference)<p>
|資格情報|[資格情報の保護と管理](../credentials-protection-and-management/credentials-protection-and-management.md)<br />現在および過去のリソースへのリンクが含まれます<p>[パスワードの概要](../kerberos/passwords-overview.md)<br />現在および過去のリソースへのリンクが含まれます|