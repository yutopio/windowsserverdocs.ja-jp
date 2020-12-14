---
description: '詳細情報: ドメイン設計の作成'
ms.assetid: 2a25bf86-a8ec-4b1a-9cbb-924d5b574481
title: フォレスト設計の作成
author: iainfoulds
ms.author: daveba
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 98d97b859765195167fdab23b9b36a69d07037cf
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049990"
---
# <a name="creating-a-domain-design"></a>フォレスト設計の作成

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

フォレストの所有者は、フォレストのドメイン設計を作成します。 ドメイン設計を作成するには、レプリケーションの要件とネットワークインフラストラクチャの既存の容量を調べ、Active Directory Domain Services (AD DS) が最も効率的な方法で機能するようにドメイン構造を構築する必要があります。 ドメインはディレクトリをパーティション分割するために使用されます。これにより、ディレクトリ内の情報を企業全体で効率的に配布し、管理することができます。 ドメイン設計の目的は、レプリケーションで使用できるネットワーク帯域幅が多すぎないようにしながら、ネットワークの日常的な操作に干渉しないように、Active Directory レプリケーショントポロジの効率を最大化することです。

## <a name="in-this-section"></a>このセクションの内容

-   [ドメインモデルの確認](../../ad-ds/plan/Reviewing-the-Domain-Models.md)

-   [必要なドメイン数を決定する](../../ad-ds/plan/Determining-the-Number-of-Domains-Required.md)

-   [既存のドメインをアップグレードするか新しいドメインを展開するかを決定する](../../ad-ds/plan/Determining-Whether-to-Upgrade-Existing-Domains-or-Deploy-New-Domains.md)

-   [ドメイン名を割り当てる](../../ad-ds/plan/Assigning-Domain-Names.md)

-   [フォレスト ルート ドメインを選択する](../../ad-ds/plan/Selecting-the-Forest-Root-Domain.md)



