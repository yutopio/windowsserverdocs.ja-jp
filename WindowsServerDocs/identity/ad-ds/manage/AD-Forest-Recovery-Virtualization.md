---
description: 詳細については、「Active Directory フォレストの回復仮想化」を参照してください。
title: AD フォレストの回復の仮想化
ms.author: daveba
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: c49b40b2-598d-49aa-85b4-766bce960e0d
ms.openlocfilehash: bf84f5db627d2383a47a9d23ce72acbc45251ea6
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049550"
---
# <a name="active-directory-forest-recovery-virtualization"></a>Active Directory フォレスト回復の仮想化

>適用対象: Windows Server 2016、Windows Server 2012、および 2012 R2、Windows Server 2008 および 2008 R2

このトピックでは、Windows Server 2016、2012 R2、および2012の仮想化ドメインコントローラーの複製機能について説明します。

## <a name="using-virtualized-domain-controller-cloning-to-expedite-forest-recovery"></a>仮想化ドメインコントローラーの複製を使用してフォレストの回復を迅速に行う

仮想化ドメインコントローラー (DC) の複製では、特に、複数の Dc がハイパーバイザー上で実行されているデータセンターなどの集中管理された場所で、追加の仮想化された Dc をドメインにインストールするプロセスを簡素化および迅速化します。 バックアップから各ドメインで1つの仮想 DC を復元すると、仮想化された DC 複製プロセスを使用して、各ドメインの追加の Dc を迅速にオンラインにすることができます。 回復する最初の仮想化 DC を準備してシャットダウンし、複製された仮想化 Dc を作成してドメインを構築するために必要な回数だけその仮想ハードディスクをコピーすることができます。

仮想化 DC の複製の要件は次のとおりです。

- ハイパーバイザーは Vm-generationid をサポートする必要があります。 Windows Server 2016、2012、および Windows 8 の hyper-v は、Vm-generationid をサポートするハイパーバイザーの一例です。 VM-GenerationID がサポートされている場合は、ハイパーバイザーベンダーに確認してください。
- 複製のソースとして使用される仮想化 DC は、Windows Server 2016 または2012を実行し、複製可能なドメインコントローラーグループのメンバーである必要があります。
- PDC エミュレーターは、Windows Server 2016 または2012を実行している必要があります。 PDC エミュレーターが仮想化されている場合は、複製できます。

仮想化 DC の複製を実行する詳細な手順については、「 [Active Directory Domain Services (AD DS) の仮想化 (レベル 100) の概要」を](../Introduction-to-Active-Directory-Domain-Services-AD-DS-Virtualization-Level-100.md)参照してください。 仮想化 DC の複製のしくみの詳細については、「 [仮想化ドメインコントローラーのテクニカルリファレンス (レベル 300)](../deploy/virtual-dc/virtualized-domain-controller-technical-reference--level-300-.md)」を参照してください。

## <a name="next-steps"></a>次のステップ

- [AD フォレストの回復 - 前提条件](AD-Forest-Recovery-Prerequisties.md)
- [AD フォレストの回復-カスタムフォレストの復旧計画の作成](AD-Forest-Recovery-Devising-a-Plan.md)
- [AD フォレストの回復-問題の特定](AD-Forest-Recovery-Identify-the-Problem.md)
- [AD フォレストの回復-回復方法を決定する](AD-Forest-Recovery-Determine-how-to-Recover.md)
- [AD フォレストの回復-最初の回復を実行する](AD-Forest-Recovery-Perform-initial-recovery.md)
- [AD フォレストの回復 - 手順](AD-Forest-Recovery-Procedures.md)
- [AD フォレストの回復-よく寄せられる質問](AD-Forest-Recovery-FAQ.md)
- [AD フォレストの回復-マルチドメインフォレスト内の単一ドメインの回復](AD-Forest-Recovery-Single-Domain-in-Multidomain-Recovery.md)
- [AD フォレストの回復-Windows Server 2003 ドメインコントローラーを使用したフォレストの回復](AD-Forest-Recovery-Windows-Server-2003.md)
