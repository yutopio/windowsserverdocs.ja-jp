---
title: AD フォレストの回復-krbtgt パスワードのリセット
description: ドメインの krbtgt パスワードをリセットする方法。
ms.author: daveba
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 3bd6c1d0-d316-4b03-b7b4-557d4537635c
ms.openlocfilehash: 0fc21aa9daf6ed528d5501f1703c847c03a8aff7
ms.sourcegitcommit: 7f859d8ec86664fdedd05901ac3714f84e7868b5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2020
ms.locfileid: "94703768"
---
# <a name="ad-forest-recovery---resetting-the-krbtgt-password"></a>AD フォレストの回復-krbtgt パスワードのリセット

> 適用対象: Windows Server 2019、Windows Server 2016、Windows Server 2012 および 2012 R2、Windows Server 2008 および 2008 R2

ドメインの krbtgt パスワードをリセットするには、次の手順に従います。 次の手順では、書き込み可能な Dc を適用しますが、読み取り専用ドメインコントローラー (Rodc) は適用しません。

> [!IMPORTANT]
> フォレストの回復中に Rodc をオンラインで回復する予定がある場合は、Rodc の krbtgt アカウントを削除しないでください。 RODC の krbtgt アカウントは krbtgt_ *number* の形式で一覧表示されます。
>
> DC でカスタマイズされたパスワードフィルター (passfilt.dll など) を使用する場合、krbtgt パスワードをリセットしようとするとエラーが発生することがあります。 回避策などの詳細については、マイクロソフトサポート技術情報の [記事 2549833](https://support.microsoft.com/kb/2549833) (を参照してください https://support.microsoft.com/kb/2549833) 。

## <a name="to-reset-the-krbtgt-password"></a>Krbtgt パスワードをリセットするには

1. [ **スタート**] をクリックし、[ **コントロールパネル**] をポイントします。次に、[ **管理ツール**] をポイントし、[ **Active Directory ユーザーとコンピューター**] をクリックします。

2. **[表示]**、 **[高度な機能]** を順にクリックします。

3. コンソールツリーで、ドメインコンテナーをダブルクリックし、[ **ユーザー**] をクリックします。

4. 詳細ウィンドウで、 **krbtgt** ユーザーアカウントを右クリックし、[ **パスワードのリセット**] をクリックします。

   ![パスワードのリセット](media/AD-Forest-Recovery-Resetting-the-krbtgt-password/resetpass1.png)

5. [ **新しいパスワード**] に新しいパスワードを入力し、[ **パスワードの確認** 入力] にパスワードを再入力して、[ **OK]** をクリックします。 指定したパスワードは、指定したパスワードとは無関係に自動的に強力なパスワードが生成されるため、重要ではありません。

> [!IMPORTANT]
> この操作は2回実行する必要があります。 キー配布センターサービスアカウントのパスワードを2回リセットすると、リセットの間に10時間の待機期間が必要になります。 **ユーザーチケットの最長有効期間** とサービスチケットポリシー設定 **の最長** 有効期間は10時間です。したがって、最大有効期間が変更されている場合、リセット間隔の最小待機時間は、構成されている値よりも大きくする必要があります。  

> [!NOTE]
> Krbtgt アカウントのパスワード履歴値は2です。つまり、2つの最新のパスワードが含まれています。 パスワードを2回リセットすると、履歴から古いパスワードが実質的にクリアされるため、別の DC がこの DC で古いパスワードを使用してレプリケートする方法はありません。

## <a name="next-steps"></a>次の手順

- [AD フォレストの回復ガイド](AD-Forest-Recovery-Guide.md)

- [AD フォレストの回復 - 手順](AD-Forest-Recovery-Procedures.md)
