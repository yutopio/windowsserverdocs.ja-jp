---
ms.assetid: f7002265-60fa-40b8-9dd7-4bf131d9320a
title: コンピューターの名前付け
author: iainfoulds
ms.author: daveba
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 1be5d49b90f9e0573054f8d541a1118516b27f01
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93068924"
---
# <a name="computer-naming"></a>コンピューターの名前付け

> 適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

Windows 2000、Windows XP、Windows Server 2003、Windows Server 2008、または Windows Vista オペレーティングシステムを実行しているコンピューターがドメインに参加している場合、既定では、そのコンピューター自体に名前が割り当てられます。 それ自体が割り当てる名前は、コンピューターのホスト名 (つまり、システムプロパティのコンピューター名) と、コンピューターが参加している (つまり、システムプロパティのプライマリ DNS サフィックス) Active Directory ドメインのドメインネームシステム (DNS) 名で構成されます。 ホスト名とドメインの DNS 名を連結したものを、完全修飾ドメイン名 (FQDN) と呼びます。 たとえば、ホスト名が Server1 のコンピューターがドメイン corp.contoso.com に参加している場合、コンピューターの FQDN は server1.corp.contoso.com になります。

DNS ゾーンに静的に入力された、または統合 DNS/動的ホスト構成プロトコル (DHCP) サーバーサービスによって登録された別の DNS ドメイン名がコンピューターに既に存在する場合、コンピューターの FQDN は、以前に登録された名前とは異なります。 コンピューターは、どちらの名前でも参照できます。

Active Directory Domain Services (AD DS) の名前付け規則の詳細については、「 [コンピューター、ドメイン、サイト、および ou の Active Directory の名前付け規則](https://support.microsoft.com/help/909264/)」を参照してください。
