---
description: '詳細情報: Winlogon 自動再起動 Sign-On (ARSO)'
title: Winlogon 自動再起動サインオン (ARSO)
ms.topic: article
ms.assetid: 15cddcfa-8a8e-45e4-bb76-b8e1a14ceac0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: 4a9aec72bd91bc28975dea1c9ba6c28cbb512c6c
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97050220"
---
# <a name="winlogon-automatic-restart-sign-on-arso"></a>Winlogon 自動再起動サインオン (ARSO)

>適用先:Windows Server (半期チャネル)、Windows Server 2016

**Author**: Justin 書籍、シニアサポートエスカレーションエンジニア (Windows グループ)

> [!NOTE]
> この内容は Microsoft カスタマー サポート エンジニアによって作成され、TechNet が通常提供しているトピックよりも詳細な Windows Server 2012 R2 の機能やソリューションの技術的説明を求めている、経験豊かな管理者とシステム設計者を対象としています。 ただし、TechNet と同様の編集過程は実施されていないため、言語によっては通常より洗練されていない文章が見られる場合があります。

## <a name="overview"></a>概要
Windows 8 では、ロック画面アプリが導入されました。  これらはアプリケーションを実行し、ユーザーのセッションのロック中に、通知を表示する (カレンダーの予定、電子メールやメッセージなどです。)。  再起動時にこれらのロック画面通知を表示するデバイスの Windows Update プロセスによって再起動が失敗します。  一部のユーザーは、これらのロック画面アプリケーションに依存します。

## <a name="whats-changed"></a>変更点は?
ユーザーが Windows 8.1 デバイスにサインインするときに LSA はユーザーの資格情報を lsass.exe によってのみアクセス可能な暗号化されたメモリに保存します。 Windows Update では、ユーザーが存在せず、自動的に再起動を開始したときはこれらの資格情報を使用して、ユーザーの自動ログオンを構成します。 TCB 特権を持つシステムとして実行されている Windows Update でこれを行う RPC 呼び出しを開始します。

ユーザーを自動的には、再起動に Autologon メカニズムを使用してサインインし、さらに、ユーザーのセッションを保護するロックされます。 資格情報の管理は LSA によって行われますが、winlogon プロセスを使用してをロックすることを行われます。  自動的に署名して、コンソールで、ユーザーのロックでは、ユーザーのロック画面アプリケーションは再起動して利用できるになります。

> [!NOTE]
> Windows Update には、再起動が強制実行され、前回の対話ユーザーが自動的にサインオンしている、セッションがロックされているそのユーザーのロック画面アプリを実行できます。

![ロック画面を示すスクリーンショット](../media/winlogon-automatic-restart-sign-on-arso/GTR_ADDS_LockScreenApp.gif)

![ロック画面のアプリを示すスクリーンショット](../media/winlogon-automatic-restart-sign-on-arso/GTR_ADDS_LockScreen.gif)

**概要**

-   Windows Update の再起動が必要

-   コンピューターを再起動することは、(*を実行中のアプリはデータは失われません*) ですか?。

    -   再起動をします。

    -   再びログインします。

    -   コンピューターのロック

-   有効になっているか、グループ ポリシーによって無効になっています

    -   Server Sku で既定で無効になっています。

-   これはなぜでしょうか。

    -   戻り、ユーザーがログオンするまで、一部の更新プログラムを終了できません。

    -   良いユーザー エクスペリエンス: 15 分の更新のインストールを完了するを待機する必要はありません

-   方法はありますか。 自動ログオン

    -   パスワードが格納されて、その資格情報では、ログインを使用

    -   ページングされたメモリに LSA シークレットとして資格情報の保存

    -   BitLocker が有効になっている場合にのみ有効にできます。

## <a name="group-policy-sign-in-last-interactive-user-automatically-after-a-system-initiated-restart"></a>グループ ポリシー: サインインが前回の対話ユーザーに自動的に再起動した後に、システムによって開始されます。
Windows 8.1/Windows Server 2012 R2、Windows Update 再起動した後に、ロック画面のユーザーの自動ログオンは Server Sku をオプトインされ、クライアントの sku の登録を取り消します。

**ポリシーの場所:** コンピューターの構成 > ポリシー > 管理用テンプレート > Windows コンポーネント > Windows のログオン オプション

**ポリシー名:** サインインが前回の対話ユーザーに自動的に再起動した後に、システムによって開始されます。

**サポートされている:** には、少なくとも Windows Server 2012 R2、Windows 8.1 または Windows RT 8.1

**説明/ヘルプ:**

このポリシー設定では、Windows Update によるシステムの再起動後にデバイスが前回の対話ユーザーで自動的にサインインするかどうかを制御します。

有効にするか、このポリシー設定を構成していない場合、デバイスは Windows Update による再起動後に自動サインインを構成するユーザーの資格情報 (ユーザー名、ドメイン、および暗号化されたパスワードを含む) を安全に保存します。 Windows Update による再起動後、ユーザーは自動的にサインインし、そのユーザー用に構成されたすべてのロック画面アプリでセッションは自動的にロックされます。

このポリシー設定を無効にした場合、デバイスでは、Windows Update による再起動後の自動サインインのためにユーザーの資格情報が保存されることはありません。 システムの再起動後、ユーザーのロック画面アプリは再起動されません。

**レジストリエディター**

|値の名前|種類|データ|
|-------|----|----|
|DisableAutomaticRestartSignOn|DWORD|0<p>**例:**<p>0 (有効)。<p>1 (無効)|

**ポリシーのレジストリの場所:** HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System

**種類:** プロシージャ

**レジストリの名前:** DisableAutomaticRestartSignOn

値: 0 または 1

0 = 有効

1 = 無効

![システム Windows Update 再起動した後に、デバイスが最後の対話ユーザーに自動的にサインインするかどうかを指定できる、ポリシー設定コントロールのスクリーンショット](../media/winlogon-automatic-restart-sign-on-arso/GTR_ADDS_SignInPolicy.gif)

## <a name="troubleshooting"></a>トラブルシューティング
WinLogon が自動的にロックしたときに WinLogon の状態のトレースは WinLogon イベント ログに格納されます。

自動ログオンの構成処理のステータスが記録されます。

-   成功した場合

    -   そのために記録します。

-   障害の場合。

    -   失敗の原因を記録します。

-   BitLocker の状態が変更されたとき。

    -   資格情報の削除がログに記録します。

        -   これらは、LSA 操作のログに保存されます。

### <a name="reasons-why-autologon-might-fail"></a>自動ログオンが失敗する理由
ユーザーの自動ログインを実現できないいくつかのケースもあります。  このセクションでは、既知のシナリオが発生する可能性がこれをキャプチャします。

### <a name="user-must-change-password-at-next-login"></a>ユーザーは次回ログイン時にパスワードを変更する必要があります。
ユーザーのログインは、次回のログイン時のパスワードの変更が必要な場合、ブロックされた状態を入力できます。  ほとんどの場合、再起動の前に検出されたすべてではなく使用できます (パスワードの有効期限の到達、シャット ダウンし、次回のログインの間です。

### <a name="user-account-disabled"></a>ユーザー アカウントを無効に
無効になっている場合でも、既存のユーザー セッションを管理できます。  再起動を無効になっているアカウントが検出されてローカルでほとんどの場合、事前にドメイン アカウントを (いくつかのドメインは、DC 上でアカウントが無効になっている場合でもにログイン シナリオの作業をキャッシュ) に、必ずしも gp に応じて。

### <a name="logon-hours-and-parental-controls"></a>ログオン時間、保護者による制限
保護者による制限とログオン時間は、作成すると、新しいユーザー セッションを禁止できます。  再起動がこの期間中に発生した場合、ユーザーはログインを許可されません。  ロックするか、対応するアクションとしてログアウトを原因となるその他のポリシーがあります。  特に、メンテナンス期間がこの期間中に一般がある場合はベッドの時間とウェイク アップのアカウントのロックダウンが発生する、多くの子の例では問題にできます。

## <a name="additional-resources"></a>その他のリソース
**テーブル SEQ テーブル \\ \* アラビア語 3: Arso 用語集**

|項目|定義|
|----|-------|
|Autologon|自動ログオンは、いくつかのリリースの Windows に存在した機能です。  これは Windows の自動ログオン v3.01 などのツールがある Windows のドキュメント化された機能 *[http:/technet.microsoft.com/sysinternals/bb963905.aspx](/sysinternals/downloads/autologon)*<p>デバイスの 1 人のユーザーの資格情報を入力しなくても自動的にサインインできます。 資格情報が構成され、暗号化された LSA シークレットとしてレジストリに格納します。|
