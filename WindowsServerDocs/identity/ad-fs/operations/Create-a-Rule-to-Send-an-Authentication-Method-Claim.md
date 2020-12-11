---
description: '詳細情報: 認証方法の要求を送信する規則を作成する'
ms.assetid: 96b9f4e6-f01c-4517-8299-017d187d447e
title: 認証方法の要求を送信する規則を作成する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: dc55613e8060eda42f5f4d47a59fc20246e1684f
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97040130"
---
# <a name="create-a-rule-to-send-an-authentication-method-claim"></a>認証方法の要求を送信する規則を作成する


" **グループメンバーシップを要求として送信** " 規則テンプレートまたは " **入力方向の要求の変換** " 規則テンプレートを使用して、認証方法の要求を送信できます。 証明書利用者は、認証方法の要求を使用して、Active Directory フェデレーションサービス (AD FS) AD FS からの要求を認証および取得するためにユーザーが使用するログオンメカニズムを決定でき \( \) ます。 また、Windows Server 2012 R2 の Active Directory フェデレーションサービス (AD FS) AD FS の認証メカニズム保証機能を \( \) 入力として使用して、証明書利用者がスマートカードログオンに基づくアクセスレベルを決定する場合の認証方法要求を生成することもできます。 たとえば、開発者は、証明書利用者アプリケーションのフェデレーションユーザーに対してさまざまなレベルのアクセス権を割り当てることができます。 アクセスのレベルは、ユーザーがスマートカードではなく、ユーザー名とパスワードの資格情報を使用してログオンしたかどうかに基づいて決まります。

組織の要件に応じて、次のいずれかの手順を実行します。

-   この規則を作成するには、" **グループメンバーシップを要求として送信** " 規則テンプレートを使用し \- ます。この規則テンプレートは、このテンプレートで指定したグループが最終的に発行する認証方法要求を決定するときに使用できます。

-   " **入力方向の要求を変換** する" 規則テンプレートを使用してこの規則を作成し \- ます。既存の認証方法を、標準の AD FS 認証方法の要求を認識しない製品で動作する新しい認証方法に変更する場合に、この規則テンプレートを使用できます。



## <a name="to-create-by-using-the-send-group-membership-as-claims-rule-template-on-a-relying-party-trust-in-windows-server-2016"></a>Windows Server 2016 の証明書利用者信頼に対して "グループメンバーシップを要求として送信する" 規則テンプレートを使用して作成するには

1.  サーバー マネージャーで、 **[ツール]** をクリックし、次に **[AD FS の管理]** を選択します。

2.  コンソールツリーの [ **AD FS** で、[ **証明書利用者の信頼**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG)

3.  \-選択した信頼を右クリックし、[**要求の発行ポリシーの編集**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule10.PNG)

4.  [ **要求発行ポリシーの編集** ] ダイアログボックスの [ **発行変換規則** ] で、[ **規則の追加** ] をクリックして規則ウィザードを開始します。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule11.PNG)

5.  [ **規則テンプレートの選択** ] ページの [ **要求規則テンプレート**] で、一覧から [ **グループメンバーシップを要求として送信** ] を選択し、[ **次へ**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group3.PNG)

6.  [ **規則の構成** ] ページで、要求規則の名前を入力します。

7.  [ **参照**] をクリックし、メンバーがこの認証方法の要求を受け取るグループを選択して、[ **OK]** をクリックします。

8.  [ **出力方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

9. [ **出力方向の要求の値**] で、次の表に示す既定の uniform resource identifier URI 値の1つを入力し \( \) ます。優先する認証方法に応じて、[ **完了**] をクリックし、[ **OK** ] をクリックして規則を保存します。

|                            実際の認証方法                             |                                対応する URI                                 |
|-------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
|                        ユーザー名とパスワードの認証                        | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password  |
|                               Windows 認証                                |  https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows  |
| \( \) X.509 証明書を使用するトランスポート層セキュリティ TLS 相互認証 | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/tlsclient |
|                  \-TLS を使用しない x.509 ベースの認証                  |   https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509    |

![ルールの作成](media/Create-a-Rule-to-Send-an-Authentication-Method-Claim/auth2.PNG)

## <a name="to-create-by-using-the-send-group-membership-as-claims-rule-template-on-a-claims-provider-trust-in-windows-server-2016"></a>Windows Server 2016 の要求プロバイダー信頼に対して "グループメンバーシップを要求として送信する" 規則テンプレートを使用して作成するには

1.  サーバー マネージャーで、 **[ツール]** をクリックし、次に **[AD FS の管理]** を選択します。

2.  コンソールツリーの [ **AD FS** で、[ **要求プロバイダー信頼**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule1.PNG)

3.  \-選択した信頼を右クリックし、[**要求規則の編集**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule2.PNG)

4.  [ **要求規則の編集** ] ダイアログボックスの [ **受け入れ変換規則** ] で、[ **規則の追加** ] をクリックして規則ウィザードを開始します。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule3.PNG)

5.  [ **規則テンプレートの選択** ] ページの [ **要求規則テンプレート**] で、一覧から [ **グループメンバーシップを要求として送信** ] を選択し、[ **次へ**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group3.PNG)

6.  [ **規則の構成** ] ページで、要求規則の名前を入力します。

7.  [ **参照**] をクリックし、メンバーがこの認証方法の要求を受け取るグループを選択して、[ **OK]** をクリックします。

8.  [ **出力方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

9. [ **出力方向の要求の値**] で、次の表に示す既定の uniform resource identifier URI 値の1つを入力し \( \) ます。優先する認証方法に応じて、[ **完了**] をクリックし、[ **OK** ] をクリックして規則を保存します。

|                            実際の認証方法                             |                                対応する URI                                 |
|-------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
|                        ユーザー名とパスワードの認証                        | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password  |
|                               Windows 認証                                |  https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows  |
| \( \) X.509 証明書を使用するトランスポート層セキュリティ TLS 相互認証 | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/tlsclient |
|                  \-TLS を使用しない x.509 ベースの認証                  |   https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509    |

![ルールの作成](media/Create-a-Rule-to-Send-an-Authentication-Method-Claim/auth2.PNG)


## <a name="to-create-this-rule-by-using-the-transform-an-incoming-claim-rule-template-on-a-relying-party-trust-in-windows-server-2016"></a>Windows Server 2016 の証明書利用者信頼で "入力方向の要求を変換する" 規則テンプレートを使用してこの規則を作成するには

1.  サーバー マネージャーで、 **[ツール]** をクリックし、次に **[AD FS の管理]** を選択します。

2.  コンソールツリーの [ **AD FS** で、[ **証明書利用者の信頼**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule9.PNG)

3.  \-選択した信頼を右クリックし、[**要求の発行ポリシーの編集**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule10.PNG)

4.  [ **要求発行ポリシーの編集** ] ダイアログボックスの [ **発行変換規則** ] で、[ **規則の追加** ] をクリックして規則ウィザードを開始します。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule11.PNG)

5.  [ **規則テンプレートの選択** ] ページの [ **要求規則テンプレート**] で、[ **入力方向の要求** を一覧から変換する] を選択し、[ **次へ**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Transform-an-Incoming-Claim/transform3.PNG)

6.  [ **規則の構成** ] ページで、要求規則の名前を入力します。

7.  [入力 **方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

8.  [ **出力方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

9. [ **入力方向の要求の値を別の出力方向の要求の値に置き換える**] を選択し、次の操作を行います。

    1.  [ **入力方向の要求の値**] に、最初に使用された実際の認証方法 uri に基づいた次のいずれかの uri 値を入力し、[ **完了**] をクリックします。次に、[ **OK** ] をクリックして規則を保存します。

    2.  [ **出力方向の要求の値**] で、次の表に示す既定の URI の値のいずれかを入力します。これは、新しい優先認証方法の選択によって異なります。 [ **完了**] をクリックし、[ **OK** ] をクリックして規則を保存します。

|              実際の認証方法              |                                対応する URI                                 |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
|         ユーザー名とパスワードの認証          | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password  |
|                 Windows 認証                 |  https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows  |
| X.509 証明書を使用する TLS 相互認証 | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/tlsclient |
|   \-TLS を使用しない x.509 ベースの認証    |   https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509    |

![ルールの作成](media/Create-a-Rule-to-Send-an-Authentication-Method-Claim/auth4.PNG)

> [!NOTE]
> テーブルの値に加えて、他の URI 値を使用することもできます。 前の表に示されている URI 値には、証明書利用者が既定で受け入れる uri が反映されています。

## <a name="to-create-this-rule-by-using-the-transform-an-incoming-claim-rule-template-on-a-claims-provider-trust-in-windows-server-2016"></a>Windows Server 2016 の要求プロバイダー信頼で "入力方向の要求の変換" 規則テンプレートを使用してこの規則を作成するには

1.  サーバー マネージャーで、 **[ツール]** をクリックし、次に **[AD FS の管理]** を選択します。

2.  コンソールツリーの [ **AD FS** で、[ **要求プロバイダー信頼**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule1.PNG)

3.  \-選択した信頼を右クリックし、[**要求規則の編集**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule2.PNG)

4.  [ **要求規則の編集** ] ダイアログボックスの [ **受け入れ変換規則** ] で、[ **規則の追加** ] をクリックして規則ウィザードを開始します。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule3.PNG)

5.  [ **規則テンプレートの選択** ] ページの [ **要求規則テンプレート**] で、[ **入力方向の要求** を一覧から変換する] を選択し、[ **次へ**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Transform-an-Incoming-Claim/transform3.PNG)

6.  [ **規則の構成** ] ページで、要求規則の名前を入力します。

7.  [入力 **方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

8.  [ **出力方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

9. [ **入力方向の要求の値を別の出力方向の要求の値に置き換える**] を選択し、次の操作を行います。

    1.  [ **入力方向の要求の値**] に、最初に使用された実際の認証方法 uri に基づいた次のいずれかの uri 値を入力し、[ **完了**] をクリックします。次に、[ **OK** ] をクリックして規則を保存します。

    2.  [ **出力方向の要求の値**] で、次の表に示す既定の URI の値のいずれかを入力します。これは、新しい優先認証方法の選択によって異なります。 [ **完了**] をクリックし、[ **OK** ] をクリックして規則を保存します。

|              実際の認証方法              |                                対応する URI                                 |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
|         ユーザー名とパスワードの認証          | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password  |
|                 Windows 認証                 |  https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows  |
| X.509 証明書を使用する TLS 相互認証 | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/tlsclient |
|   \-TLS を使用しない x.509 ベースの認証    |   https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509    |

![ルールの作成](media/Create-a-Rule-to-Send-an-Authentication-Method-Claim/auth4.PNG)























## <a name="to-create-this-rule-by-using-the-send-group-membership-as-claims-rule-template-in-windows-server-2012-r2"></a>Windows Server 2012 R2 の "グループメンバーシップを要求として送信" 規則テンプレートを使用してこの規則を作成するには

1.  サーバー マネージャーで、 **[ツール]** をクリックし、次に **[AD FS の管理]** を選択します。

2.  コンソールツリーの [AD FS の **\\ 信頼関係**] で、[ **要求プロバイダー信頼** ] または [ **証明書利用者信頼**] をクリックし、この規則を作成する一覧内の特定の信頼をクリックします。

3.  \-選択した信頼を右クリックし、[**要求規則の編集**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Pass-Through-or-Filter-an-Incoming-Claim/claimrule6.PNG)

4.  [ **要求規則の編集** ] ダイアログボックスで、編集する信頼とこの規則を作成する規則セットに応じて、次のタブのいずれかを選択し、[ **規則の追加** ] をクリックして、その規則セットに関連付けられている規則ウィザードを開始します。

    -   **受け入れ変換規則**

    -   **発行変換規則**

    -   **発行承認規則**

    -   **委任の承認規則** 
 ![ルールの作成](media/Create-a-Rule-to-Permit-All-Users/permitall5.PNG)

5.  [ **規則テンプレートの選択** ] ページの [ **要求規則テンプレート**] で、[ **グループメンバーシップを要求として送信する** ] を一覧から選択し、[ **次へ**] をクリックします。
![ルールの作成](media/Create-a-Rule-to-Send-Group-Membership-as-a-Claim/group1.PNG)

6.  [ **規則の構成** ] ページで、要求規則の名前を入力します。

7.  [ **参照**] をクリックし、メンバーがこの認証方法の要求を受け取るグループを選択して、[ **OK]** をクリックします。

8.  [ **出力方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

9. [ **出力方向の要求の値**] で、次の表に示す既定の uniform resource identifier URI 値の1つを入力し \( \) ます。優先する認証方法に応じて、[ **完了**] をクリックし、[ **OK** ] をクリックして規則を保存します。

|                            実際の認証方法                             |                                対応する URI                                 |
|-------------------------------------------------------------------------------------|----------------------------------------------------------------------------------|
|                        ユーザー名とパスワードの認証                        | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password  |
|                               Windows 認証                                |  https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows  |
| \( \) X.509 証明書を使用するトランスポート層セキュリティ TLS 相互認証 | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/tlsclient |
|                  \-TLS を使用しない x.509 ベースの認証                  |   https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509    |

![ルールの作成](media/Create-a-Rule-to-Send-an-Authentication-Method-Claim/auth1.PNG)

> [!NOTE]
> テーブルの値に加えて、他の URI 値を使用することもできます。 前の表に示す URI 値には、証明書利用者が既定で受け入れる uri が反映されています。

## <a name="to-create-this-rule-by-using-the-transform-an-incoming-claim-rule-template-in-windows-server-2012-r2"></a>Windows Server 2012 R2 で "入力方向の要求を変換する" 規則テンプレートを使用してこの規則を作成するには



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

6.  [ **規則の構成** ] ページで、要求規則の名前を入力します。

7.  [入力 **方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

8.  [ **出力方向の要求の種類**] で、一覧の [ **認証方法** ] を選択します。

9. [ **入力方向の要求の値を別の出力方向の要求の値に置き換える**] を選択し、次の操作を行います。

    1.  [ **入力方向の要求の値**] に、最初に使用された実際の認証方法 uri に基づいた次のいずれかの uri 値を入力し、[ **完了**] をクリックします。次に、[ **OK** ] をクリックして規則を保存します。

    2.  [ **出力方向の要求の値**] で、次の表に示す既定の URI の値のいずれかを入力します。これは、新しい優先認証方法の選択によって異なります。 [ **完了**] をクリックし、[ **OK** ] をクリックして規則を保存します。

|              実際の認証方法              |                                対応する URI                                 |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
|         ユーザー名とパスワードの認証          | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password  |
|                 Windows 認証                 |  https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows  |
| X.509 証明書を使用する TLS 相互認証 | https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/tlsclient |
|   \-TLS を使用しない x.509 ベースの認証    |   https://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509    |

![ルールの作成](media/Create-a-Rule-to-Send-an-Authentication-Method-Claim/auth3.PNG)

> [!NOTE]
> テーブルの値に加えて、他の URI 値を使用することもできます。 前の表に示されている URI 値には、証明書利用者が既定で受け入れる uri が反映されています。

## <a name="additional-references"></a>その他のリファレンス
[要求規則を構成する](Configure-Claim-Rules.md)

[チェックリスト:証明書利用者信頼の要求規則の作成](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913578(v=ws.11))

[チェックリスト:要求プロバイダー信頼の要求規則の作成](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/ee913564(v=ws.11))

[承認要求規則を使用するタイミング](../../ad-fs/technical-reference/When-to-Use-an-Authorization-Claim-Rule.md)

[要求の役割](../../ad-fs/technical-reference/The-Role-of-Claims.md)

[要求規則の役割](../../ad-fs/technical-reference/The-Role-of-Claim-Rules.md)
