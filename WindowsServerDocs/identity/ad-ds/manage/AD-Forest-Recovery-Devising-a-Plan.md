---
description: 'Ad フォレストの回復に関する詳細情報: AD フォレストの回復計画の考案'
title: AD フォレストの回復-AD フォレストの復旧計画の策定
ms.author: daveba
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 17381f30-55f2-4e00-977a-b701675fa4ff
ms.openlocfilehash: a1f78d060287bedd412e63231f0a9830d61afd56
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97042930"
---
# <a name="ad-forest-recovery---devising-an-ad-forest-recovery-plan"></a>AD フォレストの回復-AD フォレストの復旧計画の策定

>適用対象: Windows Server 2016、Windows Server 2012、および 2012 R2、Windows Server 2008 および 2008 R2

環境やビジネス要件によっては、このガイドで説明されているすべての手順を実行して、フォレストの回復を正常に実行する必要がある場合があります。 このガイドは、フォレストの復旧のためのテンプレートとしてのみ機能するので、環境に適したカスタムフォレストの復旧計画を作成し、ビジネスのニーズを満たすことが重要です。

たとえば、フォレストの復旧計画では、フォレストの詳細なトポロジマップが必要です。 マップには、Dc に関するすべての情報 (名前、ロールとバックアップの状態、およびそれらの間の信頼関係など) が一覧表示されます。 トポロジマップの作成に使用できるツールについては、「 [Microsoft Active Directory Topology Diagrammer](https://www.microsoft.com/download/details.aspx?id=13380)」を参照してください。

フォレストの復旧計画は、少なくとも1年に1回実行することをお勧めします。 また、Enterprise Admins グループまたは Domain Admins グループにメンバーシップの変更がある場合は、フォレストの回復訓練を実行することをお勧めします。 これにより、情報技術 (IT) スタッフがフォレストの復旧計画を完全に理解することができます。

## <a name="next-steps"></a>次の手順

- [AD フォレストの回復 - 前提条件](AD-Forest-Recovery-Prerequisties.md)
- [AD フォレストの回復-カスタムフォレストの復旧計画の作成](AD-Forest-Recovery-Devising-a-Plan.md)
- [AD フォレストの回復-問題の特定](AD-Forest-Recovery-Identify-the-Problem.md)
- [AD フォレストの回復-回復方法を決定する](AD-Forest-Recovery-Determine-how-to-Recover.md)
- [AD フォレストの回復-最初の回復を実行する](AD-Forest-Recovery-Perform-initial-recovery.md)
- [AD フォレストの回復 - 手順](AD-Forest-Recovery-Procedures.md)
- [AD フォレストの回復-よく寄せられる質問](AD-Forest-Recovery-FAQ.md)
- [AD フォレストの回復-マルチドメインフォレスト内の単一ドメインの回復](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)
- [AD フォレストの回復-Windows Server 2003 ドメインコントローラーを使用したフォレストの回復](AD-Forest-Recovery-Windows-Server-2003.md)
