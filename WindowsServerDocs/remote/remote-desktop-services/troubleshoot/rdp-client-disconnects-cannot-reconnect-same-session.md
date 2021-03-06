---
title: リモート デスクトップ クライアントが切断され、同じセッションに再接続できない
description: リモート デスクトップ クライアントが切断されて同じセッションに再接続できない問題のトラブルシューティング。
ms.reviewer: rklemen
ms.topic: troubleshooting
author: kaushika-msft
manager: dcscontentpm
ms.author: delhan
ms.date: 07/24/2019
ms.localizationpriority: medium
ms.openlocfilehash: 5cb688474482a3d97ebe07ff0ce0122d65efdd31
ms.sourcegitcommit: d5e27c1f2f168a71ae272bebf8f50e1b3ccbcca3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/23/2020
ms.locfileid: "86963194"
---
# <a name="remote-desktop-client-disconnects-and-cant-reconnect-to-the-same-session"></a>リモート デスクトップ クライアントが切断され、同じセッションに再接続できない

リモート デスクトップに対するリモート デスクトップ クライアントの接続が失われた後、クライアントがすぐに再接続できません。 ユーザーは、次のいずれかのエラーメッセージを受け取ります。

  - セキュリティ エラーのため、クライアントはターミナル サーバーに接続できませんでした。 ネットワークにサインインしていることを確認してから、接続を再試行してください。
  - リモート デスクトップが切断されました。 セキュリティ エラーのため、クライアントはリモート コンピューターに接続できませんでした。 ネットワークにログオンしていることを確認してから接続し直してください。

リモート デスクトップ クライアントが再接続すると、RDSH サーバーは、元のセッションではなく、新しいセッションにクライアントを再接続します。 ただし、RDSH サーバーを確認すると、元のセッションがまだアクティブであり、切断状態にならなかったことが示されます。

**[コンピューターの構成] > [管理用テンプレート] > [Windows コンポーネント] > [リモート デスクトップ サービス] > [リモート デスクトップ セッション ホスト] > [接続]** グループ ポリシー フォルダーで **[キープアライブ接続間隔を構成する]** ポリシーを有効にすることで、この問題を回避できます。 このポリシーを有効にした場合、キープアライブ間隔を入力する必要があります。 キープアライブ間隔で、サーバーがセッション状態を何分ごとに確認するかが決定されます。

この問題は、認証および構成設定の再構成によって修正することもできます。 これらの設定は、サーバー レベルで、またはグループ ポリシー オブジェクト (GPO) を使用して再構成できます。 設定を再構成する方法は次のとおりです。 **[コンピューターの構成]\\[管理用テンプレート]\\[Windows コンポーネント]\\[リモート デスクトップ サービス]\\[リモート デスクトップ セッション ホスト]\\[セキュリティ]** グループ ポリシー フォルダー。

1. RD セッション ホスト サーバーで、 **[リモート デスクトップ セッション ホストの構成]** を開きます。
2. **[接続]** で、接続の名前を右クリックし、 **[プロパティ]** を選択します。
3. 接続の **[プロパティ]** ダイアログ ボックスの、 **[全般]** タブの **[セキュリティ]** レイヤーで、セキュリティ メソッドを選択します。
4. **[暗号化レベル]** に移動し、必要なレベルを選択します。 **[低]** 、 **[クライアント互換]** 、 **[高]** 、または **[FIPS 準拠]** を選択できます。

> [!NOTE]  
>  - クライアントと RD セッション ホスト サーバーの間の通信で最高レベルの暗号化が必要な場合は、FIPS 準拠の暗号化を使用します。
>  - グループ ポリシーで構成した暗号化レベルの設定により、リモート デスクトップ サービス構成ツールを使用して構成した設定がオーバーライドされます。 また、[[システム暗号化: 暗号化、ハッシュ、署名のための FIPS 準拠アルゴリズムを使う]](/windows/security/threat-protection/security-policy-settings/system-cryptography-use-fips-compliant-algorithms-for-encryption-hashing-and-signing) ポリシーを有効にした場合、この設定により **[クライアント接続の暗号化レベルを設定する]** ポリシーがオーバーライドされます。 システム暗号化ポリシーは、 **[コンピューターの構成] > [Windows の設定] > [セキュリティ設定] > [ローカル ポリシー] > [セキュリティ オプション]** フォルダーにあります。
>  - 暗号化レベルを変更した場合、新しい暗号化レベルは、ユーザーが次回サインインした時に有効になります。 1 つのサーバーで複数の暗号化レベルが必要な場合は、複数のネットワーク アダプターをインストールし、各アダプターを個別に構成します。
>  - 対応する秘密キーが証明書にあることを確認するには、リモート デスクトップ サービスの構成に移動し、証明書を表示する接続を右クリックして、 **[全般]** 、 **[編集]** の順に選択します。 その後、 **[証明書の表示]** を選択します。 **[全般]** タブに移動すると、キーが存在する場合は、"この証明書に対応する秘密キーを持っています" と表示されるはずです。 また、この情報は、証明書スナップインを使用して表示することもできます。
>  - FIPS 準拠の暗号化 ( **[システム暗号化: 暗号化、ハッシュ、署名のための FIPS 準拠アルゴリズムを使う]** ポリシーまたはリモート デスクトップ サーバーの構成の **[FIPS 準拠]** の設定) では、Microsoft 暗号化モジュールを使用する Federal Information Processing Standard (FIPS) 140-1 暗号化アルゴリズムで、サーバーとクライアントの間で送信されるデータが暗号化および暗号化解除されます。 詳しくは、「[FIPS 140 検証](/windows/security/threat-protection/fips-140-validation)」をご覧ください。
>  - **[高]** の設定では、強力な 128 ビット暗号化を使って、サーバーとクライアントの間で送信されるデータが暗号化されます。
>  - **[クライアント互換]** の設定では、クライアントとサーバーの間で送信されるすべてのデータが、クライアントでサポートされている最高のキー強度で暗号化されます。
>  - **[低]** の設定では、56 ビット暗号化を使って、クライアントからサーバーに送信されるデータが暗号化されます。
