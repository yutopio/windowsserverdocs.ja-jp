---
description: 詳細については、「コンピューターをドメインに参加させる」を参照してください。
ms.assetid: 10d6723e-c857-43da-9d2d-acb5641d3da8
title: コンピューターをドメインに参加させる
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 20c7971ff64792deadbb453edd4a76f02b14bd98
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97042126"
---
# <a name="join-a-computer-to-a-domain"></a>コンピューターをドメインに参加させる

Active Directory フェデレーションサービス (AD FS) \( AD FS \) を機能させるには、フェデレーションサーバーとして機能する各コンピューターがドメインに参加している必要があります。 フェデレーションサーバープロキシはドメインに参加することができますが、これは必須ではありません。

Web サーバーが要求対応アプリケーションのみをホストしている場合は、Web サーバーをドメインに参加させる必要はありません \- 。

この手順を完了するには、ローカル コンピューター上の **Administrators** または同等のメンバーシップが最低限必要です。  適切なアカウントおよびグループメンバーシップの使用方法の詳細については、「 [ローカルおよびドメインの既定のグループ](https://go.microsoft.com/fwlink/?LinkId=83477)」を参照してください。

### <a name="to-join-a-computer-to-a-domain"></a>コンピューターをドメインに参加させるには

1.  [ **スタート** ] 画面で「 **コントロールパネル**」と入力し、enter キーを押します。

2.  [ **システムとセキュリティ**] に移動し、[ **システム**] をクリックします。

3.  [**コンピューター名、ドメインおよびワークグループの設定**] で [**設定の変更**] をクリックします。

4.  **[コンピューター名]** タブで、**[変更]** をクリックします。

5.  [次 **のメンバー**] で [ **ドメイン**] をクリックし、このコンピューターを参加させるドメインの名前を入力して、[ **OK]** をクリックします。

6.  **[OK]** をクリックし、コンピューターを再起動します。

## <a name="additional-references"></a>その他のリファレンス
[チェックリスト:フェデレーション サーバーのセットアップ](Checklist--Setting-Up-a-Federation-Server.md)

[チェックリスト:フェデレーション サーバー プロキシのセットアップ](Checklist--Setting-Up-a-Federation-Server-Proxy.md)


