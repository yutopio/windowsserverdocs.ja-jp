---
description: 詳細については、「Windows Server 2016 の Active Directory Domain Services の新機能」を参照してください。
ms.assetid: 6a852428-c1ec-4703-b3b3-a4bfdf8cbb9d
title: Windows Server 2016 での Active Directory Domain Services の新機能
ms.author: joflore
author: MicrosoftGuyJFlo
manager: mtillman
ms.date: 08/07/2018
ms.topic: article
ms.openlocfilehash: d13e4f64d0e73d9066bf0c614e8c653b94a6db1e
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97050060"
---
# <a name="whats-new-in-active-directory-domain-services-for-windows-server-2016"></a>Windows Server 2016 の Active Directory Domain Services の新機能

>適用先:Windows Server 2016

Active Directory Domain Services (AD DS) の次の新機能により、組織は Active Directory 環境を保護し、クラウドのみのデプロイとハイブリッドデプロイに移行できるようになります。一部のアプリケーションとサービスはクラウドでホストされ、他のアプリケーションとサービスはオンプレミスでホストされます。 WebJobs からの改善点は、以下のとおりです。

- [Privileged access management](/microsoft-identity-manager/pam/privileged-identity-management-for-active-directory-domain-services)

- [Azure Active Directory 参加を使用したクラウド機能の Windows 10 デバイスへの拡張](/azure/active-directory/devices/overview)

- [Windows 10 エクスペリエンスのためにドメイン参加済みデバイスを Azure AD に接続する](/azure/active-directory/devices/hybrid-azuread-join-plan)

- [組織での Microsoft Passport for Work の有効化](/windows/security/identity-protection/hello-for-business/hello-identity-verification)

- [ファイルレプリケーションサービス (FRS) と Windows Server 2003 の機能レベルの廃止](ad-ds/active-directory-functional-levels.md)

## <a name="privileged-access-management"></a>Privileged access management

Privileged access management (PAM) は、ハッシュ、スピアーフィッシング、同様の種類の攻撃など、資格情報の盗難手法によって発生する Active Directory 環境のセキュリティの問題を軽減するのに役立ちます。 Microsoft Identity Manager (MIM) を使用して構成された新しい管理アクセスソリューションを提供します。 PAM の導入:

- 新しい要塞 Active Directory フォレスト。 MIM によってプロビジョニングされます。 要塞フォレストには、既存のフォレストとの特別な PAM 信頼があります。 これにより、悪意のあるアクティビティがないことがわかっている新しい Active Directory 環境が提供され、特権アカウントを使用するために既存のフォレストから分離されます。

- 管理特権を要求する MIM の新しいプロセスと、要求の承認に基づいて新しいワークフローを作成します。

- 管理者特権の要求に応じて、MIM によって要塞フォレストにプロビジョニングされた新しいシャドウセキュリティプリンシパル (グループ)。 シャドウセキュリティプリンシパルには、既存のフォレスト内の管理グループの SID を参照する属性があります。 これにより、シャドウグループは、アクセス制御リスト (Acl) を変更することなく、既存のフォレスト内のリソースにアクセスできるようになります。

- 期限切れのリンク機能。シャドウグループの時間制限のメンバーシップを有効にします。 管理タスクを実行するために必要な時間だけ、ユーザーをグループに追加することができます。 タイムアウトしたメンバーシップは、Kerberos チケットの有効期間に反映される time-to-live (TTL) 値によって表されます。

    > [!NOTE]
    > 期限切れのリンクは、リンクされているすべての属性で使用できます。 ただし、PAM などの完全なソリューションで、期限切れリンク機能を使用するように事前構成されている唯一の例として、グループとユーザーの間のメンバー/memberOf のリンクされた属性リレーションシップがあります。

- KDC の機能強化は Active Directory ドメインコントローラーに組み込まれています。これにより、ユーザーが管理グループに複数の時間バインドメンバーシップを持っている場合に Kerberos チケットの有効期限 (TTL) の値を制限することができます。 たとえば、時間にバインドされたグループ A に追加した場合、ログオン時に Kerberos チケット保証チケット (TGT) の有効期間はグループ A の残りの時間と同じになります。また、グループ A よりも TTL が低い別のタイムバインドグループ B のメンバーである場合は、TGT の有効期間はグループ B の残りの時間と同じになります。

- アクセスの要求者、付与されたアクセス、実行されたアクティビティを簡単に識別できる新しい監視機能。

### <a name="requirements-for-privileged-access-management"></a>Privileged access management の要件

- Microsoft Identity Manager

- Active Directory Windows Server 2012 R2 以降のフォレストの機能レベル。

## <a name="azure-ad-join"></a>Azure AD Join

Azure Active Directory Join を使用すると、企業や個人のデバイスの機能が向上し、enterprise、business、EDU の各顧客の id エクスペリエンスが向上します。

利点:

- 企業所有の Windows デバイスで **最新の設定を利用** できます。 酸素 Services は、個人の Microsoft アカウントを必要としなくなりました。コンプライアンスを確保するために、ユーザーの既存の職場アカウントを使用して実行されるようになりました。 酸素 Services は、オンプレミスの Windows ドメインに参加している Pc と、Azure AD テナント ("クラウドドメイン") に "参加" している Pc とデバイスで動作します。 設定は次のとおりです。

   - ローミングまたは個人用設定、ユーザー補助の設定および資格情報
   - バックアップと復元
   - 職場アカウントを使用した Microsoft Store へのアクセス
   - ライブタイルと通知

- Windows ドメインに参加できないモバイルデバイス (携帯電話、タブレット) の **組織のリソースにアクセス** します。これは、企業所有か byod かにかかわらず、Windows ドメインに参加することはできません。
- Office 365 およびその他の組織のアプリ、web サイト、リソースに **シングルサイン** オンします。
- **BYOD デバイスで** は、(オンプレミスのドメインまたは Azure AD から) 個人所有のデバイスに職場アカウントを追加して、条件付きアカウント制御やデバイスの正常性構成証明などの新しい機能に確実に準拠させることができるように、アプリと web で作業リソースの SSO を利用できます。
- **Mdm 統合** を使用すると、Mdm (Intune またはサードパーティ) にデバイスを自動登録できます。
- 組織内の複数のユーザーに対して **、"キオスク" モードと共有デバイスを設定** します。
- **開発者エクスペリエンス** を使用すると、共有されたプログラミングスタックで企業と個人の両方のコンテキストに対応するアプリを構築できます。
- **イメージング** オプションを使用すると、イメージングを選択し、ユーザーが最初の実行時に企業所有のデバイスを直接構成できるようにすることができます。

詳細については、「 [Azure Active Directory でのデバイス管理の概要](/azure/active-directory/devices/overview)」を参照してください。

## <a name="windows-hello-for-business"></a>Windows Hello for Business

Windows Hello for Business は、パスワード以外のキーベースの認証方法である組織とコンシューマーです。 この形式の認証では、侵害、盗難、phish のある資格情報に依存しています。

ユーザーは、証明書または非対称キーペアにリンクされている情報を使用して、生体認証または PIN のログを使用してデバイスにログオンします。 Id プロバイダー (IDPs) は、ユーザーの公開キーを Idps にマップし、ワンタイムパスワード (OTP)、電話、または別の通知メカニズムを使用してログオン情報を提供することによって、ユーザーを検証します。

詳細については、「 [Windows Hello For Business](/windows/security/identity-protection/hello-for-business/hello-identity-verification) 」を参照してください。

## <a name="deprecation-of-file-replication-service-frs-and-windows-server-2003-functional-levels"></a>ファイルレプリケーションサービス (FRS) と Windows Server 2003 の機能レベルの廃止

ファイルレプリケーションサービス (FRS) と Windows Server 2003 の機能レベルは、以前のバージョンの Windows Server では非推奨とされていましたが、Windows Server 2003 オペレーティングシステムのサポートは終了しています。 その結果として、Windows Server 2003 を実行するすべてのドメイン コントローラーを、ドメインから削除する必要があります。 以前のバージョンの Windows Server を実行しているドメインコントローラーが環境に追加されないようにするには、ドメインとフォレストの機能レベルを少なくとも Windows Server 2008 に上げる必要があります。

Windows Server 2008 以上のドメイン機能レベルでは、分散ファイル サービス (DFS) レプリケーションを使用して、ドメイン コントローラー間で SYSVOL フォルダーの内容をレプリケートします。 Windows Server 2008 ドメイン機能レベル以上で新しいドメインを作成した場合、SYSVOL のレプリケートには DFS レプリケーションが自動的に使用されます。 それより低い低い機能レベルでドメイン作成した場合は、SYSVOL のレプリケーションを FRS から DFS に移行する必要があります。 移行手順については、 [次の手順](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/dd640019\(v=ws.10\)) に従うか、 [ストレージチームのファイルキャビネットのブログで合理化](https://techcommunity.microsoft.com/t5/storage-at-microsoft/bg-p/FileCAB)された一連の手順を参照することができます。

Windows Server 2003 のドメインとフォレストの機能レベルは引き続きサポートされますが、SYSVOL レプリケーションの互換性とサポートを将来的に保証するために、機能レベルを Windows Server 2008 (またはそれ以上) に引き上げる必要があります。 さらに、より高い機能レベルで利用可能な他の多くの利点と機能もあります。 詳細については、次のリソースを参照してください。

- [Active Directory Domain Services (AD DS) の機能レベルとは](ad-ds/active-directory-functional-levels.md)
- [ドメインの機能レベルを上げる](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc753104\(v=ws.11\))
- [フォレストの機能レベルを上げる](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc730985\(v=ws.11\))
