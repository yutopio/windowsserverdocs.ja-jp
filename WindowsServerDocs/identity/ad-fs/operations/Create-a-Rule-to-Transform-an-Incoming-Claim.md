---
description: '詳細情報: 入力方向の要求を変換するルールを作成する'
ms.assetid: ef83960f-d2cf-441f-b2b6-d97822ec7149
title: 入力方向の要求を変換する規則を作成する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 7dbb6ca59de0d7a9c3e696084409323e743b27f1
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97040040"
---
# <a name="create-a-rule-to-transform-an-incoming-claim"></a>入力方向の要求を変換する規則を作成する


Active Directory フェデレーションサービス (AD FS) AD FS の [ **入力方向の要求の変換** ] 規則テンプレートを使用すると、 \( \) 入力方向の要求を選択し、その要求の種類を変更して、その要求の値を変更できます。 たとえば、この規則テンプレートを使用して、入力方向のグループ要求と同じ要求値を持つロール要求を送信するルールを作成できます。 また、管理者という値を持つ入力方向のグループ要求がある場合、この規則を使用して、要求値が購入者のグループ要求を送信することもできます。また、で終わるユーザープリンシパル名 UPN 要求のみを送信することもでき \( \) @fabrikam ます。

AD FS 管理スナップインを使用して要求規則を作成するには、次の手順を実行 \- します。

この手順を実行するには、ローカルコンピューターの **Administrators**、またはそれと同等のメンバーシップが最低限必要です。  適切なアカウントおよびグループメンバーシップの使用方法の詳細については、「 [ローカルおよびドメインの既定のグループ](https://go.microsoft.com/fwlink/?LinkId=83477)」を参照してください。

## <a name="to-create-a-rule-to-transform-an-incoming-claim-on-a-relying-party-trust-in-windows-server-2016"></a>Windows Server 2016 で証明書利用者信頼の入力方向の要求を変換する規則を作成するには

1.  サーバー マネージャーで、 **[ツール]** をクリックし、次に **[AD FS の管理]** を選択します。

2.  コンソールツリーの [ **AD FS** で、[ **証明書利用者の信頼**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG)

3.  \-選択した信頼を右クリックし、[**要求の発行ポリシーの編集**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule10.PNG)

4.  [ **要求発行ポリシーの編集** ] ダイアログボックスの [ **発行変換規則** ] で、[ **規則の追加** ] をクリックして規則ウィザードを開始します。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule11.PNG)

5.  [ **規則テンプレートの選択** ] ページの [ **要求規則テンプレート**] で、[ **入力方向の要求** を一覧から変換する] を選択し、[ **次へ**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Transform-an-Incoming-Claim/transform3.PNG)

6.  [ **規則の構成** ] ページの [ **要求規則名**] に、この規則の表示名を入力します。 [入力 **方向の要求の種類**] で、一覧から要求の種類を選択します。 [ **出力方向の要求の種類**] で、一覧から要求の種類を選択し、組織の要件に応じて次のいずれかのオプションを選択します。

    -   **すべての要求値をパススルーする**

    -   **入力方向の要求の値を、別の出力方向の要求の値に置き換える**

    -   **受信し \- た電子メールサフィックス要求を新しい電子 \- メールサフィックスで置き換える規則を** 
 ![ 作成する](media/Create-a-Rule-to-Transform-an-Incoming-Claim/transform4.PNG)

7.  **[完了]** をクリックします。

8.  [ **要求規則の編集** ] ダイアログボックスで、[ **OK** ] をクリックして規則を保存します。

> [!NOTE]
> AD FS 発行された要求を使用する動的 Access Control シナリオを設定する場合は、 \- 最初に要求プロバイダー信頼に対して変換規則を作成し、[入力 **方向** の要求の種類] に入力方向の要求の名前を入力します。または、要求の説明が既に作成されている場合は、一覧から選択します。 次に、[ **出力方向の要求の種類**] で、目的の要求 URL を選択し、デバイス要求を発行するための変換規則を証明書利用者信頼に対して作成します。
>
> 動的 Access Control シナリオの詳細については、「 [動的 Access Control コンテンツロードマップ](../../solution-guides/dynamic-access-control--scenario-overview.md) 」または「 [AD FS での AD DS 要求の使用](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831504(v=ws.11))」を参照してください。

## <a name="to-create-a-rule-to-transform-an-incoming-claim-on-a-claims-provider-trust-in-windows-server-2016"></a>Windows Server 2016 で要求プロバイダー信頼の入力方向の要求を変換する規則を作成するには

1.  サーバー マネージャーで、 **[ツール]** をクリックし、次に **[AD FS の管理]** を選択します。

2.  コンソールツリーの [ **AD FS** で、[ **要求プロバイダー信頼**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule1.PNG)

3.  \-選択した信頼を右クリックし、[**要求規則の編集**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule2.PNG)

4.  [ **要求規則の編集** ] ダイアログボックスの [ **受け入れ変換規則** ] で、[ **規則の追加** ] をクリックして規則ウィザードを開始します。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule3.PNG)

5.  [ **規則テンプレートの選択** ] ページの [ **要求規則テンプレート**] で、[ **入力方向の要求** を一覧から変換する] を選択し、[ **次へ**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Transform-an-Incoming-Claim/transform3.PNG)

6.  [ **規則の構成** ] ページの [ **要求規則名**] に、この規則の表示名を入力します。 [入力 **方向の要求の種類**] で、一覧から要求の種類を選択します。 [ **出力方向の要求の種類**] で、一覧から要求の種類を選択し、組織の要件に応じて次のいずれかのオプションを選択します。

    -   **すべての要求値をパススルーする**

    -   **入力方向の要求の値を、別の出力方向の要求の値に置き換える**

    -   **受信し \- た電子メールサフィックス要求を新しい電子 \- メールサフィックスで置き換える規則を** 
 ![ 作成する](media/Create-a-Rule-to-Transform-an-Incoming-Claim/transform4.PNG)

7.  **[完了]** をクリックします。

8.  [ **要求規則の編集** ] ダイアログボックスで、[ **OK** ] をクリックして規則を保存します。

> [!NOTE]
> AD FS 発行された要求を使用する動的 Access Control シナリオを設定する場合は、 \- 最初に要求プロバイダー信頼に対して変換規則を作成し、[入力 **方向** の要求の種類] に入力方向の要求の名前を入力します。または、要求の説明が既に作成されている場合は、一覧から選択します。 次に、[ **出力方向の要求の種類**] で、目的の要求 URL を選択し、デバイス要求を発行するための変換規則を証明書利用者信頼に対して作成します。
>
> 動的 Access Control シナリオの詳細については、「 [動的 Access Control コンテンツロードマップ](../../solution-guides/dynamic-access-control--scenario-overview.md) 」または「 [AD FS での AD DS 要求の使用](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831504(v=ws.11))」を参照してください。

## <a name="to-create-a-rule-to-transform-an-incoming-claim-in-windows-server-2012-r2"></a>Windows Server 2012 R2 で入力方向の要求を変換するルールを作成するには

1.  サーバーマネージャーで、[ **ツール**] をクリックし、[ **AD FS の管理**] をクリックします。

2.  コンソールツリーの [AD FS の **\\ 信頼関係**] で、[ **要求プロバイダー信頼** ] または [ **証明書利用者信頼**] をクリックし、この規則を作成する一覧内の特定の信頼をクリックします。

3.  \-選択した信頼を右クリックし、[**要求規則の編集**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule6.PNG)

4.  [ **要求規則の編集** ] ダイアログボックスで、次のいずれかのタブを選択します。このタブは、編集している信頼と、この規則を作成する規則セットによって異なります。次に、[ **規則の追加** ] をクリックして、その規則セットに関連付けられている規則ウィザードを開始します。

    -   **受け入れ変換規則**

    -   **発行変換規則**

    -   **発行承認規則**

    -   **委任の承認規則** 
 ![ルールの作成](media/Create-a-Rule-to-Permit-All-Users/permitall5.PNG)

5.  [ **規則テンプレートの選択** ] ページの [ **要求規則テンプレート**] で、[ **入力方向の要求** を一覧から変換する] を選択し、[ **次へ**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Transform-an-Incoming-Claim/transform1.PNG)

6.  [ **規則の構成** ] ページの [ **要求規則名**] に、この規則の表示名を入力します。 [入力 **方向の要求の種類**] で、一覧から要求の種類を選択します。 [ **出力方向の要求の種類**] で、一覧から要求の種類を選択し、組織の要件に応じて次のいずれかのオプションを選択します。

    -   **すべての要求値をパススルーする**

    -   **入力方向の要求の値を、別の出力方向の要求の値に置き換える**

    -   **受信し \- た電子メールサフィックス要求を新しい電子 \- メールサフィックスで置き換える規則を** 
 ![ 作成する](media/Create-a-Rule-to-Transform-an-Incoming-Claim/transform2.PNG)

> [!NOTE]
> AD FS 発行された要求を使用する動的 Access Control シナリオを設定する場合は、 \- 最初に要求プロバイダー信頼に対して変換規則を作成し、[入力 **方向** の要求の種類] に入力方向の要求の名前を入力します。または、要求の説明が既に作成されている場合は、一覧から選択します。 次に、[ **出力方向の要求の種類**] で、目的の要求 URL を選択し、デバイス要求を発行するための変換規則を証明書利用者信頼に対して作成します。
>
> 動的 Access Control シナリオの詳細については、「 [動的 Access Control コンテンツロードマップ](../../solution-guides/dynamic-access-control--scenario-overview.md) 」または「 [AD FS での AD DS 要求の使用](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831504(v=ws.11))」を参照してください。

7. **[完了]** をクリックします。

8. [ **要求規則の編集** ] ダイアログボックスで、[ **OK** ] をクリックして規則を保存します。

## <a name="additional-references"></a>その他のリファレンス
[要求規則を構成する](Configure-Claim-Rules.md)

[チェックリスト:証明書利用者信頼の要求規則の作成](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913578(v=ws.11))

[チェックリスト:要求プロバイダー信頼の要求規則の作成](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913564(v=ws.11))

[承認要求規則を使用するタイミング](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)

[要求の役割](../../ad-fs/technical-reference/The-Role-of-Claims.md)

[要求規則の役割](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md)
