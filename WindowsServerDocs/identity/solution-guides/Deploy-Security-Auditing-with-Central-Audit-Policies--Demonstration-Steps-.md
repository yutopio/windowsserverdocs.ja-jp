---
description: 詳細については、「集約型監査ポリシーを使用したセキュリティ監査の展開 (デモンストレーション手順)」を参照してください。
ms.assetid: 22347a94-aeea-44b4-85fb-af2c968f432a
title: 集約型の監査ポリシーを使用したセキュリティ監査の展開 (デモンストレーション手順)
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 6d55fc8b1d7a1f1c7f94b09c773a079f3488862c
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97046500"
---
# <a name="deploy-security-auditing-with-central-audit-policies-demonstration-steps"></a>集約型の監査ポリシーを使用したセキュリティ監査の展開 (デモンストレーション手順)

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

このシナリオでは、「 [集約型アクセスポリシーの展開 &#40;デモンストレーション手順&#41;](Deploy-a-Central-Access-Policy--Demonstration-Steps-.md)」で作成した finance ポリシーを使用して、finance ドキュメントフォルダー内のファイルへのアクセスを監査します。 このフォルダーへのアクセスが許可されていないユーザーがこのフォルダーにアクセスしようとすると、イベント ビューアーでそのアクティビティがキャプチャされます。
このシナリオをテストするには、次の手順が必要です。

|タスク|説明|
|--------|---------------|
|[グローバル オブジェクト アクセスの構成](Deploy-Security-Auditing-with-Central-Audit-Policies--Demonstration-Steps-.md#BKMK_1)|この手順では、ドメイン コントローラーでグローバル オブジェクト アクセス ポリシーを構成します。|
|[グループポリシーの設定を更新する](Deploy-Security-Auditing-with-Central-Audit-Policies--Demonstration-Steps-.md#BKMK_2)|ファイル サーバーにサインインし、グループ ポリシーの更新を適用します。|
|[グローバル オブジェクト アクセス ポリシーが適用されたことの検証](Deploy-Security-Auditing-with-Central-Audit-Policies--Demonstration-Steps-.md#BKMK_3)|イベント ビューアーで関連するイベントを確認します。 これらのイベントには、国とドキュメント タイプのメタデータが含まれている必要があります。|

## <a name="configure-global-object-access-policy"></a><a name="BKMK_1"></a>グローバル オブジェクト アクセス ポリシーの構成
この手順では、ドメイン コントローラーでグローバル オブジェクト アクセス ポリシーを構成します。

#### <a name="to-configure-a-global-object-access-policy"></a>グローバル オブジェクト アクセス ポリシーを構成するには

1. パスワードを使用して、contoso\administrator としてドメインコントローラー DC1 にサインインし <strong>pass@word1</strong> ます。

2. サーバー マネージャーで、**[ツール]** をポイントし、**[グループ ポリシーの管理]** をクリックします。

3. コンソール ツリーで、**[ドメイン]**、**[contoso.com]** の順にダブルクリックし、**[Contoso]** をクリックして、**[ファイル サーバー]** をダブルクリックします。

4. **[FlexibleAccessGPO]** を右クリックし、**[編集]** をクリックします。

5. **[コンピューターの構成]**、**[ポリシー]**、**[Windows の設定]** の順にダブルクリックします。

6. **[セキュリティの設定]**、**[監査ポリシーの詳細な構成]**、**[監査ポリシー]** の順にダブルクリックします。

7. **[オブジェクト アクセス]**、**[ファイル システムの監査]** の順にダブルクリックします。

8. **[次の監査イベントを構成する]** チェック ボックスをオンにし、**[成功]** チェック ボックスと **[失敗]** チェック ボックスをオンにして、**[OK]** をクリックします。

9. ナビゲーション ウィンドウで、**[グローバル オブジェクト アクセスの監査]**、**[ファイル システム]** の順にダブルクリックします。

10. **[このポリシーの設定を定義する]** チェック ボックスをオンにし、**[構成]** をクリックします。

11. **[グローバル ファイルの SACL のセキュリティの詳細設定]** ボックスで、**[追加]**、**[プリンシパルの選択]** の順にクリックし、「**Everyone**」と入力して、**[OK]** をクリックします。

12. **[グローバル ファイルの SACL の監査エントリ]** ボックスで、**[アクセス許可]** ボックスの **[フル コントロール]** をクリックします。

13. **[条件の追加]** セクションで **[条件の追加]** をクリックし、ドロップダウン リストで **[リソース]****[部署]****[次のいずれか]****[値]****[財務]** をクリックします。

14. **[OK]** を 3 回クリックして、グローバル オブジェクト アクセス監査ポリシー設定の構成を完了します。

15. ナビゲーション ウィンドウで **[オブジェクト アクセス]** をクリックし、結果ウィンドウで **[ハンドル操作の監査]** をダブルクリックします。 **[次の監査イベントを構成する]**、**[成功]**、**[失敗]** をクリックして **[OK]** をクリックし、柔軟なアクセス GPO を閉じます。

## <a name="update-group-policy-settings"></a><a name="BKMK_2"></a>グループ ポリシー設定の更新
この手順では、監査ポリシーを作成した後でグループ ポリシー設定を更新します。

#### <a name="to-update-group-policy-settings"></a>グループ ポリシーの設定を更新するには

1. パスワードを使用して、contoso\Administrator としてファイルサーバー FILE1 にサインインし <strong>pass@word1</strong> ます。

2. Windows キーを押しながら R キーを押し、「**cmd**」と入力してコマンド プロンプト ウィンドウを開きます。

   > [!NOTE]
   > [**ユーザー アカウント制御**] ダイアログ ボックスが表示されたら、表示された操作が正しいことを確認し、[**はい**] をクリックします。

3. 「**gpupdate /force**」と入力し、Enter キーを押します。

## <a name="verify-that-the-global-object-access-policy-has-been-applied"></a><a name="BKMK_3"></a>グローバル オブジェクト アクセス ポリシーが適用されたことの検証
グループ ポリシーの設定が適用された後、監査ポリシーの設定が正しく適用されたことを検証できます。

#### <a name="to-verify-that-the-global-object-access-policy-has-been-applied"></a>グローバル オブジェクト アクセス ポリシーが適用されたことを検証するには

1.  クライアント コンピューター CLIENT1 に Contoso\MReid としてサインインします。 フォルダーのハイパーリンク "file:/// \\ \\ \\ \ ID_AD_FILE1 \\ & Finance" \\ \ file1\finance documents Documents を参照し、Word 文書2を変更します。

2.  contoso\administrator としてファイル サーバー FILE1 にサインインします。 イベント ビューアーを開き、**[Windows ログ]** に移動して **[セキュリティ]** をクリックし、アクティビティの結果として監査イベント **4656** と **4663** が発生したことを確認します (作成、変更、または削除したファイルまたはフォルダーについて明示的な監査 SACL を設定しなかった場合でも、これらの監査イベントが発生します)。

> [!IMPORTANT]
> 有効なアクセス許可が確認されているユーザーのために、リソースが配置されているコンピューター上で新しいログオン イベントが生成されます。 ユーザー サインイン アクティビティのセキュリティ監査ログを分析する場合、有効なアクセス許可が原因となって生成されるログオン イベントと対話型のネットワーク ユーザー サインインが原因となって生成されるログオン イベントを区別するために、偽装レベル情報が含められます。 有効なアクセス許可が原因となってログオン イベントが生成される場合、偽装レベルは Identity です。 対話型のネットワーク ユーザー サインインでは、通常、偽装レベルが Impersonation または Delegation のログオン イベントが生成されます。

## <a name="see-also"></a><a name="BKMK_Links"></a>関連項目

-   [シナリオ: ファイル アクセスの監査](Scenario--File-Access-Auditing.md)

-   [ファイル アクセスの監査の計画](Plan-for-File-Access-Auditing.md)

-   [ダイナミック アクセス制御: シナリオの概要](Dynamic-Access-Control--Scenario-Overview.md)


