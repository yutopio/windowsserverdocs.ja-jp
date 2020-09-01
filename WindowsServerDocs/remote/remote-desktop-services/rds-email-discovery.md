---
title: RDS フィードに登録するために電子メールの検出を設定する
description: RDS 展開にメール検出をセットアップする方法を説明します。
ms.author: chrimo
ms.date: 8/28/2020
ms.localizationpriority: medium
ms.topic: article
author: christianmontoya
ms.openlocfilehash: 71b892d95b15f02445ec7898a6c57f931bc4b501
ms.sourcegitcommit: 2b1a12c85acff137e5ac84cd0e62d8353fcdde31
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2020
ms.locfileid: "89087465"
---
# <a name="set-up-email-discovery-to-subscribe-to-your-rds-feed"></a>RDS フィードに登録するために電子メールの検出を設定する

フィード URL 内の単一の文字が不足している、または URL が含まれる電子メールを紛失したという理由で、エンドユーザーが各自に発行された RDS フィードに接続できないというトラブルを経験したことがありますか。 ほぼすべてのリモート デスクトップ クライアント アプリケーションでは、電子メール アドレスの入力によるサブスクリプションの検索をサポートして、ユーザーが各自の RemoteApp とデスクトップに簡単に接続できるようにしています。

電子メールの検出を設定する前に、以下を行います。

- 電子メールに関連付けられているドメインに TXT レコードを追加する権限があるかどうかを確認します (たとえば、ユーザーの電子メール アドレスに @contoso.com が含まれている場合は、contoso.com ドメインへのアクセス許可が必要です)。
- RD Web フィード URL (https://\<rdweb-dns-name\>.domain/RDWeb/Feed/webfeed.aspx (例: https://rdweb.contoso.com/RDWeb/Feed/webfeed.aspx) ) を作成します。

>[!NOTE]
>リモート デスクトップではなく Windows Virtual Desktop を使用している場合は、代わりに次の URL を使用します。
>
>- Windows Virtual Desktop (クラシック) を使用している場合: <https://rdweb.wvd.microsoft.com/api/feeddiscovery/webfedddiscovery.aspx>
>- Windows Virtual Desktop を使用している場合: <https://rdweb.wvd.microsoft.com/api/arm/feeddiscovery>

次に、以下の手順に従って、電子メールの検出を設定します。

1. ブラウザーで、ドメインが登録されているドメイン名レジストラーの Web サイトに接続します。
2. DNS レコードを表示、追加、および編集できる登録済みのドメイン用の適切なページに移動します.
3. 次のプロパティを持つ新しい DNS レコードを入力します。
   - **ホスト:** _msradc
   - **テキスト:** \<RD Web Feed URL\>
   - **TTL:** 300

   DNS レコードのフィールドの名前はドメイン名レジストラーによって異なりますが、このプロセスでは、RD Web フィード全体の値を持つ _msradc.\<domain_name\> (_msradc.contoso.com など) という名前の TXT レコードになります。

以上で作業は終了です。 ここでデバイス上のリモート デスクトップ アプリケーションを起動して、ご自身を登録してください。