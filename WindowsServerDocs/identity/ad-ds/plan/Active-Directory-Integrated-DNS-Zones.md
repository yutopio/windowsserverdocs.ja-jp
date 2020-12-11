---
description: 詳細については、「Active Directory-Integrated DNS ゾーン数」を参照してください。
ms.assetid: 39c0126d-af5e-4dcb-88c1-aa38f888e973
title: Active Directory 統合 DNS ゾーン
author: iainfoulds
ms.author: daveba
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: d07e6ae9751d299cb2f81edb20b036a1cfe63048
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97050130"
---
# <a name="active-directory-integrated-dns-zones"></a>Active Directory 統合 DNS ゾーン

> 適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

ドメインコントローラー上で実行されているドメインネームシステム (DNS) サーバーは、Active Directory Domain Services (AD DS) にゾーンを格納できます。 この方法では、すべてのゾーンデータが Active Directory レプリケーションによって自動的にレプリケートされるため、通常の DNS ゾーン転送を使用する別の DNS レプリケーショントポロジを構成する必要はありません。 これにより、DNS の展開プロセスが簡略化され、次のような利点があります。

- DNS レプリケーション用に複数のマスターが作成されます。 そのため、DNS サーバーサービスを実行しているドメイン内のドメインコントローラーは、そのドメインが権限を持っているドメイン名に対して、Active Directory 統合された DNS ゾーンの更新を書き込むことができます。 別の DNS ゾーン転送トポロジは必要ありません。

- セキュリティで保護された動的更新がサポートされています。 セキュリティで保護された動的更新を使用すると、管理者は、コンピューターの名前を更新したり、許可されていないコンピューターが DNS 内の既存の名前を上書きすることを防ぐ

Windows Server 2008 の Active Directory 統合 DNS では、ゾーンデータがアプリケーションディレクトリパーティションに格納されます。 (Active Directory との Windows Server 2003 ベースの DNS 統合から動作が変更されることはありません)。AD DS のインストール時に、次の DNS 固有のアプリケーションディレクトリパーティションが作成されます。

- ForestDnsZones と呼ばれるフォレスト全体のアプリケーションディレクトリパーティション

- ドメイン全体のアプリケーションディレクトリパーティション (DomainDnsZones という名前のフォレスト内の各ドメイン用)

AD DS がアプリケーションパーティションに DNS 情報を格納する方法の詳細については、「 [Dns テクニカルリファレンス](/previous-versions/windows/it-pro/windows-server-2003/cc779926(v=ws.10))」を参照してください。

> [!NOTE]
> Active Directory ドメインサービスインストールウィザード (Dcpromo.exe) を実行する場合は、DNS をインストールすることをお勧めします。 これを行うと、ウィザードによって自動的に DNS ゾーンの委任が作成されます。 詳細については、「 [Windows Server 2008 のフォレストルートドメインの展開](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc731174(v=ws.10))」を参照してください。
