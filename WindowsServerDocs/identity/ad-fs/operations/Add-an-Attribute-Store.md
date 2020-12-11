---
description: 詳細については、「属性ストアの追加」を参照してください。
ms.assetid: c60227a8-7b44-40f8-b807-a6532851a4a6
title: 属性ストアを追加する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 3672d80b89738b10bcd0e0ef186b33592d6b53e2
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97044280"
---
# <a name="add-an-attribute-store"></a>属性ストアを追加する


Active Directory フェデレーションサービス (AD FS) AD FS によって保護されているリソースへのアクセスを必要とするユーザーアカウントとコンピューターアカウント \( \) は、Active Directory Domain Services AD DS などの属性ストアに格納され \( \) ます。 要求発行エンジンは、属性ストアを使用して、要求を発行するために必要なデータを収集します。 その後、属性ストアからのデータが要求として投影されます。

属性ストアをフェデレーションサービスに追加するには、次の手順を実行します。

この手順を完了するには、ローカル コンピューター上の **Administrators** または同等のメンバーシップが最低限必要です。  適切なアカウントおよびグループメンバーシップの使用方法の詳細については、「 [ローカルおよびドメインの既定のグループ](https://go.microsoft.com/fwlink/?LinkId=83477)」を参照してください。

#### <a name="to-add-an-attribute-store"></a>属性ストアを追加するには

1.  **AD FS 管理** を開きます。

2.  [ **アクション** ] で [ **属性ストアの追加**] をクリックします。

![属性ストアの追加](media/Add-an-Attribute-Store/addstore1.PNG)

3. [ **属性ストアの追加** ] ダイアログボックスで、追加する属性ストアの次のプロパティを構成します。

   -   [ **表示名**] に、属性ストアを識別するために使用する名前を入力します。

   -   [ **属性ストアの種類**] で、サポートされている属性ストアの種類として、 **Active Directory**、 **LDAP**、または **SQL** のいずれかを選択します。

   -   [ **接続文字列**] で、ライトウェイトディレクトリアクセスプロトコル LDAP ストアまたは構造化照会言語 SQL ストアのいずれかを選択した場合は、 \( \) \( \) 属性ストアへの接続の確立に使用した文字列を入力します。 Active Directory の属性ストアの場合、接続文字列は必要ありません。このため、このフィールドは無効になっています。

       > [!NOTE]
       > AD FS の既定の設定では、Active Directory 属性ストアが自動的に作成されます。

![属性ストアの追加](media/Add-an-Attribute-Store/addstore2.PNG)

4. **[OK]** をクリックします。

## <a name="additional-references"></a>その他のリファレンス

[AD FS の運用](../ad-fs-operations.md)

[属性ストアの役割](../../ad-fs/technical-reference/The-Role-of-Attribute-Stores.md)
