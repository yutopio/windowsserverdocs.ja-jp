---
ms.assetid: c32606b4-2ee2-4df3-a704-8ac6723e188f
title: DNS と AD DS
ms.author: daveba
author: iainfoulds
manager: daveba
ms.date: 08/08/2018
ms.topic: article
ms.openlocfilehash: 65157b564f5d1a30a0a76f0ab11e7eaca6135f7d
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93069494"
---
# <a name="dns-and-ad-ds"></a>DNS と AD DS

> 適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

Active Directory Domain Services (AD DS) は、ドメインネームシステム (DNS) の名前解決サービスを使用して、クライアントがドメインコントローラーを特定し、ディレクトリサービスをホストするドメインコントローラーが相互に通信できるようにします。

AD DS により、Active Directory 名前空間を既存の DNS 名前空間に簡単に統合できます。 Active Directory 統合された DNS ゾーンなどの機能を使用すると、セカンダリゾーンを設定する必要がなくなり、ゾーン転送を構成しなくても、DNS を簡単に展開できるようになります。

DNS が AD DS をサポートする方法の詳細については、「 [Active Directory テクニカルリファレンスの Dns サポート](/previous-versions/windows/it-pro/windows-server-2003/cc781627(v=ws.10))」セクションを参照してください。

> [!NOTE]
> AD DS ドメイン名がクライアントが使用するプライマリ DNS サフィックスとは異なる名前空間を実装した場合、DNS との統合 AD DS より複雑になります。 詳細については、「 [不整合な名前空間](Disjoint-Namespace.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

- [ドメイン コントローラーの場所](Domain-Controller-Location.md)
- [Active Directory 統合 DNS ゾーン](Active-Directory-Integrated-DNS-Zones.md)
- [コンピューターの名前付け](Computer-Naming.md)
- [名前空間の不整合](Disjoint-Namespace.md)
