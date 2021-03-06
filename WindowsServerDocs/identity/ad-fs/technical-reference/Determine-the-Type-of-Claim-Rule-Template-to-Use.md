---
description: '詳細情報: 使用する要求規則テンプレートの種類を決定する'
ms.assetid: 696a29b2-d627-4c9a-a384-9c8aaf50bd23
title: 使用する要求規則テンプレートの種類を決定する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: a3609ee6676f2db2ad3007509bbd81f70d68014a
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97042390"
---
# <a name="determine-the-type-of-claim-rule-template-to-use"></a>使用する要求規則テンプレートの種類を決定する


Active Directory フェデレーションサービス (AD FS) AD FS インフラストラクチャの設計の重要な部分 \( \) は、組織とのフェデレーションに参加する各パートナーに対して、要求規則の完全なセットと、それらを作成するために使用する必要がある対応する要求規則テンプレートを決定することです。 規則を作成するには、AD FS 管理スナップインで要求規則テンプレートを使用し \- ます。

構成する各要求規則セットと関連付けることができるフェデレーションによる信頼は 1 つだけです。 つまり、ある信頼に対して作成した規則のセットを、フェデレーション サービスの他の信頼に対して使用することはできません。 それより、要求規則テンプレートから規則を作成する方が簡単であり、各フェデレーション パートナーと組織の間で合意される、必要な要求のセットをすばやく生成できます。

規則と規則テンプレートの詳細については、「 [The Role of Claim Rules](The-Role-of-Claim-Rules.md)」をご覧ください。

使用する要求規則テンプレートの種類の決定を始める前に、次の点を検討してください。

-   信頼される要求プロバイダーによってどのような要求が提供されますか

-   各要求プロバイダーのどのような要求を信頼しますか

-   このフェデレーション サービスを信頼する証明書利用者はどのような要求が必要ですか

-   各証明書利用者にはどのような要求を公開しますか

-   各証明書利用者にアクセスできる必要があるユーザーは誰ですか

これらの質問に答えることは、信頼性の高い要求規則の設計を計画するのに役立ちます。 また、円滑な承認とアクセス制御戦略の作成、および展開チームによるロールアウトの効率化にも有効です。

次のセクションでは、ビジネス ルールに基づいて選択する規則テンプレートの種類について説明します。

## <a name="claim-rule-template-types"></a>要求規則テンプレートの種類
次の表では、AD FS 管理スナップインを使用して規則を作成するために使用できるすべての種類の要求規則テンプレートと、別の種類のテンプレートを使用する利点について説明し \- ます。

|規則テンプレートの種類|説明|長所|短所|
|----------------------|---------------|--------------|-----------------|
|入力方向の要求を通すか、フィルター処理する|選択された要求種類のすべての要求値をそのまま通す規則、または要求値に基づいて要求をフィルター処理し、選択された要求種類の特定の要求値のみをそのまま通す規則を作成するために使用します。<p>詳細については、「 [When to Use a Pass Through or Filter Claim Rule](When-to-Use-a-Pass-Through-or-Filter-Claim-Rule.md)」を参照してください。|-受け入れまたは変更せずに発行する特定の要求を選択するために使用できます。|-要求の種類と値を変更することはできません|
|入力方向の要求を変換する|入力方向の要求を選択して、異なる要求種類にマップできる規則、またはその要求値を新しい要求値にマップできる規則を作成するために使用します。<p>詳細については、「 [When to Use a Transform Claim Rule](When-to-Use-a-Transform-Claim-Rule.md)」を参照してください。|-要求の種類または値を正規化するために使用できます。<br />- \- 入力方向の要求の電子メールサフィックスを置き換えることができます。|-複雑な文字列の置換にはカスタムルールが必要です|
|LDAP 属性を要求として送信する|LDAP 属性ストアから属性を選択し、要求として証明書利用者に送信する規則を作成するために使用します。<p>詳細については、「 [When to Use a Send LDAP Attributes as Claims Rule](When-to-Use-a-Send-LDAP-Attributes-as-Claims-Rule.md)」を参照してください。|-任意の AD DS \/ AD LDS 属性ストアから要求を送信できます<br />-1 つのルールを使用して複数の要求を発行できます。|-パフォーマンス-アカウント参照の結果として低速<br />-クエリにカスタム LDAP フィルターを使用することはできません|
|グループ メンバーシップを要求として送信する|ユーザーが Active Directory セキュリティ グループのメンバーである場合に指定された要求の種類と値を送信できる規則を作成するために使用します。 この規則を使用すると、選択したグループに基づいて、1 つの要求だけが送信されます。<p>詳細については、「 [When to Use a Send Group Membership as a Claim Rule](When-to-Use-a-Send-Group-Membership-as-a-Claim-Rule.md)」を参照してください。|-グループ要求を発行するための高速なパフォーマンス–アカウント参照なし|-ユーザーはローカル Active Directory グループのメンバーである必要があります|
|カスタム規則を使用して要求を送信する|標準的な規則テンプレートより高度なオプションを提供するカスタム規則を作成するために使用します。 AD FS 要求規則言語を使用して、カスタム規則を記述します。<p>詳細については、「 [When to Use a Custom Claim Rule](When-to-Use-a-Custom-Claim-Rule.md)」を参照してください。|-SQL 属性ストアから要求を送信するために使用できます。<br />-カスタム LDAP フィルターを指定するために使用できます<br />-PPID を発行するために使用できます<br />-カスタム属性ストアで使用できます。<br />-入力要求セットにのみ要求を追加するために使用できます<br />-複数の入力方向の要求に基づいて要求を送信するために使用できます。|- \- 最初に要求規則言語に関する情報を取得するために、一部の増加率を構成することが困難な場合があります。|
|入力方向の要求に基づくユーザーの許可または拒否|入力方向の要求の種類と値に基づいて、証明書利用者へのユーザーによるアクセスを許可または拒否する規則を作成するために使用します。<p>詳細については、「 [When to Use an Authorization Claim Rule](When-to-Use-an-Authorization-Claim-Rule.md)」を参照してください。|-承認プロセスを簡略化します。|-要求の種類と要求の値を1つだけ指定する必要があります<br />-要求値のパターンマッチングはサポートしていません|
|すべてのユーザーを許可|すべてのユーザーに証明書利用者へのアクセスを許可する規則を作成するために使用します。<p>詳細については、「 [When to Use an Authorization Claim Rule](When-to-Use-an-Authorization-Claim-Rule.md)」を参照してください。|-構成が簡単|-受信要求テンプレートに基づいてユーザーを許可または拒否するよりも安全性が低くなります。|


