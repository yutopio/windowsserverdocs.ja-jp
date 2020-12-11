---
description: 詳細については、「信頼の1側での信頼パスワードのリセット」を参照してください。
title: AD フォレストの回復-信頼できるパスワードのリセット
ms.author: daveba
author: iainfoulds
manager: daveba
ms.date: 08/09/2018
ms.topic: article
ms.assetid: 398918dc-c8ab-41a6-a377-95681ec0b543
ms.openlocfilehash: 6ed37c1e85d097602c52c3448a4c1e6e6128cd1e
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97041550"
---
# <a name="resetting-a-trust-password-on-one-side-of-the-trust"></a>信頼の1側での信頼されたパスワードのリセット

>適用対象: Windows Server 2016、Windows Server 2012、および 2012 R2、Windows Server 2008 および 2008 R2

 フォレストの回復がセキュリティ侵害に関連している場合は、次の手順を使用して、信頼の一方の側で信頼されたパスワードをリセットします。 これには、子ドメインと親ドメイン間の暗黙的な信頼と、このドメイン (信頼する側のドメイン) と別のドメイン (信頼される側のドメイン) との間の明示的な信頼が含まれます。

 信頼の信頼する側のドメイン側 (このドメインが属する側) でのみパスワードをリセットします。 次に、信頼されているドメイン側 (出力方向の信頼とも呼ばれます) で同じパスワードを使用します。 他の (信頼されている) ドメインのそれぞれで最初の DC を復元するときに、出力方向の信頼のパスワードをリセットします。

 信頼のパスワードをリセットすると、DC がドメインの外部に存在する可能性のある Dc にレプリケートされなくなります。 各ドメインの最初の DC を復元するときに同じ信頼のパスワードを設定することにより、この DC が復旧された各 Dc と確実にレプリケートされるようになります。 AD DS のインストールによって回復されるドメイン内の後続の Dc は、インストールプロセス中にこれらの新しいパスワードを自動的にレプリケートします。

## <a name="to-reset-a-trust-password-on-one-side-of-the-trust"></a>信頼の一方の側で信頼のパスワードをリセットするには

1. コマンド プロンプトで次のコマンドを入力し、Enter キーを押します。

   ```
   netdom experthelp trust
   ```

2. このコマンドによって提供される構文を使用して、NetDom ツールを使用して信頼のパスワードをリセットします。
   たとえば、フォレスト内に親と子の2つのドメインがあり、親ドメインの復元された DC でこのコマンドを実行している場合は、次のコマンド構文を使用します。

   ```
   netdom trust parent domain name /domain:child domain name /resetOneSide /passwordT:password /userO:administrator /passwordO:*
   ```

   子ドメインでこのコマンドを実行する場合は、次のコマンド構文を使用します。

   ```
   netdom trust child domain name /domain:parent domain name /resetOneSide /passwordT:password /userO:administrator /passwordO:*
   ```

   > [!NOTE]
   > **Passwordt** は、信頼の両側で同じ値にする必要があります。 このコマンドは、パスワードを2回自動的にリセットするため、( **netdom resetpwd** コマンドとは異なり) 1 回だけ実行します。

## <a name="next-steps"></a>次の手順

- [AD フォレストの回復ガイド](AD-Forest-Recovery-Guide.md)
- [AD フォレストの回復 - 手順](AD-Forest-Recovery-Procedures.md)
