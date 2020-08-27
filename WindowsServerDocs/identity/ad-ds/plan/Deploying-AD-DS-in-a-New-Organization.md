---
ms.assetid: a589dda6-e05b-4b44-ae3e-b15dd3877617
title: 新しい組織の AD DS の展開
author: iainfoulds
ms.author: iainfou
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 5d412c6bb4740d34dcd2c66ea0a899a8c286b148
ms.sourcegitcommit: 1dc35d221eff7f079d9209d92f14fb630f955bca
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/26/2020
ms.locfileid: "88941472"
---
# <a name="deploying-ad-ds-in-a-new-organization"></a>新しい組織の AD DS の展開

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

Active Directory Domain Services (AD DS) 設計を十分に準備することは、コスト効果の高い展開に不可欠です。 現在、ネットワーク環境がディレクトリサービスなしで運用されている場合は、AD DS をデプロイする前に、AD DS 論理構造の包括的な設計を行ってください。 次に、新しいフォレストルートドメインを展開し、設計に応じて残りのドメイン構造をデプロイできます。

次の図は、ディレクトリサービスを使用せずに現在動作しているネットワーク環境に Windows Server 2008 AD DS を展開する手順を示しています。

![新しい組織への展開](media/Deploying-AD-DS-in-a-New-Organization/daa38971-86f2-4033-9442-0cdff9ecc48f.gif)

新しい組織で AD DS を計画および展開するために使用できる詳細なタスクの一覧については、「 [チェックリスト: 新しい組織への AD DS の展開](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc725897(v=ws.10))」を参照してください。

