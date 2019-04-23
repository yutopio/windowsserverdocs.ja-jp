---
ms.assetid: c81b8291-fba5-4b30-a43d-7feb2f4b66be
title: Windows Server 2012 R2 での AD FS 設計ガイド
description: ''
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.prod: windows-server-threshold
ms.technology: identity-adfs
ms.openlocfilehash: f618add4c4803142b3bd7278908834a412f30999
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59862573"
---
# <a name="identify-your-ad-fs-deployment-goals"></a>AD FS 展開目標の特定

>適用先:Windows Server 2016、Windows Server 2012 R2

Active Directory フェデレーション サービスを正しく特定する\(AD FS\)展開の目標は、AD FS の設計プロジェクトの成功に不可欠です。 優先順位を付けるし、場合によっては、結合、展開の目標、設計し、反復的なアプローチを使用して AD FS を展開することができます。 文書化、および AD FS のデザインに関連して、状況に応じて実用的な解決策を開発する AD FS 展開目標の定義済みの既存の利用できます。  
  
AD FS の以前のバージョンは、次を実現するためにデプロイされた最もよく。  
  
-   Web の従業員または顧客を提供する\-、SSO が発生する要求にアクセスするときに\-ベースのアプリケーションは、企業内で。  
  
-   Web の従業員または顧客を提供する\-ベースの SSO エクスペリエンスをフェデレーション パートナー組織のリソースにアクセスします。  
  
-   Web の従業員または顧客を提供する\-SSO が発生する Web サイトやサービスにリモート アクセスする内部でホストされている場合。  
  
-   Web の従業員または顧客を提供する\-SSO が発生するリソースまたはクラウド内のサービスにアクセスする場合。  
  
これらに加えて、Windows Server® 2012 R2 で AD FS には、以下を実現するのに役立つ機能が追加されます。  
  
-   SSO およびシームレスな 2 要素認証のためのデバイス社内参加。 これにより、ユーザーの個人のデバイスからのアクセスを許可し、このアクセスを提供するときに、リスクを管理する組織です。  
  
-   マルチによるリスク管理\-アクセス制御を考慮します。 AD FS では、だれがどのアプリケーションにアクセスするかを制御する承認レベルが充実しています。 ユーザー属性に基づいてこのできます\(UPN、電子メール、セキュリティ グループのメンバーシップ、認証強度など\)、デバイス属性\(かどうか、デバイスは、社内参加している\)の属性を要求または\(ネットワークの場所、IP アドレス、またはユーザー エージェント\)します。  
  
-   その他のマルチによるリスク管理\-機密性の高いアプリケーションの要素認証。 AD FS では、可能性のあるマルチを要求するポリシーを制御できます。\-要素では、グローバルに、またはアプリケーションごとを認証します。 さらに、AD FS は、複数の機能拡張ポイントを提供\-に緊密な統合をセキュリティで保護されたでシームレスな複数の要素認証ベンダー\-のエンド ユーザー エクスペリエンスを考慮します。  
  
-   Web アプリケーション プロキシで保護されている、エクストラネットからの web リソースにアクセスするためには、認証および承認機能を提供します。  
  
要約すると、組織内の次の目標を達成するために Windows Server 2012 R2 で AD FS を展開できます。  
  
### <a name="enable-your-users-to-access-resources-on-their-personal-devices-from-anywhere"></a>どこからでも、個人のデバイス上のリソースにアクセスするユーザーを有効にします。  
  
-   社内参加: ユーザー個人のデバイスが企業の Active Directory に参加できるため、そのデバイスから企業のリソースにシームレスにアクセスできます。  
  
-   プレ\-Web アプリケーション プロキシで保護され、インターネットからアクセスされる企業ネットワーク内のリソースの認証。  
  
-   社内参加デバイスからのパスワード変更: パスワードの有効期限が切れたときに、ユーザーが引き続きリソースにアクセスできるように、任意の社内参加デバイスからパスワードを変更できます。  
  
### <a name="enhance-your-access-control-risk-management-tools"></a>アクセス制御リスク管理ツールを強化します。  
リスク管理は、どの IT 組織にとってもガバナンスおよびコンプライアンスの面で重要です。 ある多数のアクセス制御リスク管理に関する機能強化、Windows Server® 2012 R2 で AD FS で、次を含みます。  
  
-   柔軟な制御は、AD FS にアクセスするユーザーを認証する方法を制御するネットワークの場所に基づく\-アプリケーションをセキュリティで保護します。  
  
-   ユーザーが複数を実行する必要があるかどうかを決定する柔軟なポリシー\-要素認証、ユーザーのデータ、デバイス データ、およびネットワークの場所に基づいています。  
  
-   あたり\-SSO を無視し、機密性の高いアプリケーションにアクセスするたびに資格情報を提供するユーザーを強制的にアプリケーションが制御します。  
  
-   ごとの柔軟な\-ユーザー データ、デバイス データ、またはネットワークの場所に基づいて、アプリケーションのアクセス ポリシー。  
  
-   AD FS のエクストラネット ロックアウト。管理者がインターネットのブルート フォース攻撃から Active Directory アカウントを保護できます。  
  
-   Active Directory で無効化されているか削除されている、社内参加対応デバイスに対するアクセスの失効。  
  
### <a name="use-ad-fs-to-enhance-the-sign-in-experience"></a>AD FS を使用して、サインインを強化する\-エクスペリエンス  
次に Windows Server® 2012 R2 で AD FS 機能をカスタマイズおよびサインインを強化するには管理者を有効にする新しい\-エクスペリエンス。  
  
-   AD FS サービスの統合カスタマイズ。一度行った変更は、指定されたファームの残りの AD FS フェデレーション サーバーに自動的に反映されます。  
  
-   署名更新\-最新の外観し、自動的にさまざまなフォーム ファクターに対応するページ。  
  
-   サポート フォームへの自動フォールバック\-ベースの認証に会社のドメインに参加していないが、まだ使用されているデバイスが企業ネットワーク内からアクセス要求を生成\(イントラネット\)します。  
  
-   シンプルなコントロールで、会社のロゴ、画像、IT サポートへの標準リンク、ホーム ページ、プライバシーなどをカスタマイズ。  
  
-   説明のカスタマイズのメッセージ署名で\-ページ。  
  
-   Web テーマのカスタマイズ。  
  
-   ホーム領域検出\(HRD\)会社のパートナーのプライバシーを強化するユーザーの組織サフィックスに基づいています。  
  
-   HRD フィルタ リング、あたり\-アプリケーションに基づいて、アプリケーションごと、領域を自動的に選択します。  
  
-   1 つ\-エラー レポートを簡単をクリックします。 IT のトラブルシューティング。  
  
-   カスタマイズ可能なエラー メッセージ。  
  
-   ユーザー認証の選択 (複数の認証プロバイダーが使用可能な場合)。  
  
## <a name="see-also"></a>関連項目  
[Windows Server 2012 R2 で AD FS 設計ガイドします。](../../ad-fs/design/AD-FS-Design-Guide-in-Windows-Server-2012-R2.md)  
  
