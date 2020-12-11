---
description: AD フォレストの回復-DC でコンピューターアカウントをリセットする方法の詳細について説明します。
title: AD フォレストの回復-DC でコンピューターアカウントをリセットする
ms.author: daveba
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 4e1a6070-df0a-4dfe-8773-899a010bfabd
ms.openlocfilehash: 21d36989ff6174e5b59eed0b6b63e8aea0a9d921
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97041570"
---
# <a name="ad-forest-recovery---resetting-the-computer-account-on-the-dc"></a>AD フォレストの回復-DC でコンピューターアカウントをリセットする

>適用対象: Windows Server 2016、Windows Server 2012、および 2012 R2、Windows Server 2008 および 2008 R2

 DC のコンピューターアカウントのパスワードをリセットするには、次の手順に従います。

## <a name="to-reset-the-computer-account-password-of-the-domain-controller"></a>ドメインコントローラーのコンピューターアカウントのパスワードをリセットするには

1. コマンド プロンプトで次のコマンドを入力し、Enter キーを押します。

   ```
   netdom help resetpwd
   ```

2. 次の例のように、Netdom コマンドラインツールを使用してコンピューターアカウントのパスワードをリセットするために、このコマンドで提供される構文を使用します。

   ```
   netdom resetpwd /server:domain controller name /userD:administrator /passwordd:*
   ```

    ここで、 *ドメインコントローラー名* は、回復しているローカル DC です。

   > [!NOTE]
   > このコマンドは2回実行する必要があります。

## <a name="next-steps"></a>次の手順

- [AD フォレストの回復ガイド](AD-Forest-Recovery-Guide.md)
- [AD フォレストの回復 - 手順](AD-Forest-Recovery-Procedures.md)
