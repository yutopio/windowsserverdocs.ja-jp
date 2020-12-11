---
description: 詳細については、「Windows Server の AD FS で要求規則を構成する」を参照してください。
ms.assetid: 9cafa3e1-8118-4a75-a7c2-1dbe40b1a444
title: 要求規則の構成
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: edf9e7c2bdcb93e3f838addf3149d06a3c632fc1
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97045440"
---
# <a name="configure-claim-rules-in-ad-fs-for-windows-server"></a>Windows Server の AD FS で要求規則を構成する

要求ベースの \- id モデルで \( \) は、フェデレーションサービスとして AD FS Active Directory フェデレーションサービス (AD FS) の機能は、一連の要求を含むトークンを発行することになります。 要求規則は、AD FS 問題が発生したクレームに関する決定を制御します。 要求規則とすべてのサーバー構成データは、AD FS 構成データベースに格納されます。

AD FS は、要求とその他のコンテキスト情報の形式で提供される id 情報に基づいて、発行の決定を行います。 大まかには、AD FS は、1セットの要求を入力として取得し、さまざまな変換を実行して、出力として別のクレームセットを返すことによって、ルールプロセッサとして動作します。

次のトピックは、AD FS が処理するルールを作成する際に役立ちます。

-   [入力方向の要求をパススルーまたはフィルター処理するルールを作成する](Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim.md)

-   [すべてのユーザーを許可する規則を作成する](Create-a-Rule-to-Permit-All-Users.md)

-   [入力方向の要求に基づいてユーザーを許可または拒否する規則を作成する](Create-a-Rule-to-Permit-or-Deny-Users-Based-on-an-Incoming-Claim.md)

-   [LDAP 属性を要求として送信するルールを作成する](Create-a-Rule-to-Send-LDAP-Attributes-as-Claims.md)

-   [グループ メンバーシップを要求として送信する規則を作成する](Create-a-Rule-to-Send-Group-Membership-as-a-Claim.md)

-   [入力方向の要求を変換する規則を作成する](Create-a-Rule-to-Transform-an-Incoming-Claim.md)

-   [認証方法の要求を送信する規則を作成する](Create-a-Rule-to-Send-an-Authentication-Method-Claim.md)
-   [AD FS 1.x と互換性のある要求を送信するルールを作成する](Create-a-Rule-to-Send-an-AD-FS-1x-Compatible-Claim.md)

-   [カスタム規則を使用して要求を送信する規則を作成する](Create-a-Rule-to-Send-Claims-Using-a-Custom-Rule.md)

## <a name="see-also"></a>関連項目
[AD FS の運用](../ad-fs-operations.md)
