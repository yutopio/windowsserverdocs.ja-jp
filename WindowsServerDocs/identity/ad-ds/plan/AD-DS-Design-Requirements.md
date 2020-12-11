---
description: '詳細情報: AD DS 設計要件'
ms.assetid: f6e76ef0-2217-4cdb-980f-22a780a85ebb
title: AD DS の設計の要件
author: iainfoulds
ms.author: daveba
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 244f11e30e5c17f86dab6e8eee8ff8313e9d065f
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97050150"
---
# <a name="ad-ds-design-requirements"></a>AD DS の設計の要件

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012


## <a name="designing-the-active-directory-logical-structure"></a>Active Directory 論理構造の設計
Windows Server 2008 Active Directory Domain Services (AD DS) を展開する前に、環境に合わせて AD DS 論理構造を計画し、設計する必要があります。 AD DS 論理構造は、ディレクトリオブジェクトの編成方法を決定し、ネットワークアカウントと共有リソースを管理するための効果的な方法を提供します。 AD DS の論理構造を設計する際には、組織のネットワークインフラストラクチャの重要な部分を定義します。

AD DS 論理構造を設計するには、組織が必要とするフォレストの数を決定し、ドメイン、ドメインネームシステム (DNS) インフラストラクチャ、および組織単位 (Ou) の設計を作成します。 次の図は、論理構造を設計するプロセスを示しています。

![AD DS 設計要件](media/AD-DS-Design-Requirements/d5cebae6-a752-4063-a98f-473799c251bd.gif)

詳細については、「 [Windows Server 2008 AD DS の論理構造の設計](Designing-the-Logical-Structure.md)」を参照してください。

## <a name="designing-the-site-topology"></a>サイトトポロジの設計
AD DS インフラストラクチャの論理構造を設計したら、ネットワークのサイトトポロジを設計する必要があります。 サイトトポロジは、物理ネットワークを論理的に表したものです。 AD DS サイトの場所、各サイト内の AD DS ドメインコントローラー、サイト間の AD DS レプリケーションをサポートするサイトリンクとサイトリンクブリッジに関する情報が含まれています。 次の図は、サイトトポロジの設計プロセスを示しています。

![AD DS 設計要件](media/AD-DS-Design-Requirements/d34d43c0-437f-47cb-9b64-09c0f9ce6479.gif)

詳細については、「 [Windows Server 2008 用のサイトトポロジの設計 AD DS](Designing-the-Site-Topology.md)」を参照してください。

## <a name="planning-domain-controller-capacity"></a>ドメインコントローラーの容量の計画
効率的な AD DS パフォーマンスを確保するには、各サイトの適切な数のドメインコントローラーを特定し、Windows Server 2008 のハードウェア要件を満たしていることを確認する必要があります。 ドメインコントローラーの容量計画を慎重に行うことで、ハードウェア要件を過小使用しないようにすることができます。これにより、ドメインコントローラーのパフォーマンスとアプリケーションの応答時間が低下する可能性があります。 次の図は、ドメインコントローラーの容量計画のプロセスを示しています。

![AD DS 設計要件](media/AD-DS-Design-Requirements/fff6ef22-5c7b-4478-ad76-42b296dcf769.gif)

## <a name="enabling-windows-server-2008-advanced-ad-ds-features"></a>Windows Server 2008 の高度な AD DS 機能を有効にする
Windows Server 2008 AD DS を使用すると、ドメインまたはフォレストの機能レベルを上げることで、環境に高度な機能を導入できます。 ドメインまたはフォレスト内のすべてのドメインコントローラーが Windows Server 2008 を実行している場合は、機能レベルを Windows Server 2008 に上げることができます。

詳細については、「 [AD DS の高度な機能の有効化](../../ad-ds/plan/Enabling-Advanced-Features-for-AD-DS.md)」を参照してください。



