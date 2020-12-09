---
title: 通知の制限を構成する
description: この記事では、さまざまな通知の種類ごとに時間制限を設定する方法を説明します。
ms.date: 7/7/2017
ms.topic: article
author: JasonGerend
manager: brianlic
ms.author: jgerend
ms.openlocfilehash: 625fb9c6a36717e57f3c6fd6da696b8df07fe8c3
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96866061"
---
# <a name="configure-notification-limits"></a>通知の制限を構成する

> 適用対象: Windows Server (半期チャネル)、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2

クォータのしきい値の超過や承認されていないファイルの保存などに関する通知は、繰り返し何度も発生することがあります。このような通知が頻繁に発生することを抑えるため、ファイル サーバー リソース マネージャーでは、次の種類の通知について時間の制限が適用されています。

-   電子メール
-   イベント ログ
-   コマンド
-   レポート

これらの各制限により、構成対象の種類の通知は、最初の通知が生成された後、指定した時間が経過するまで同一の問題についての 2 回目の通知は生成されません。

既定では、それぞれの通知の種類ごとに 60 分の制限が設定されていますが、この値は変更することができます。 制限は、クォータのしきい値に関する通知であるか、ファイルのスクリーン処理イベントに関する通知であるかを問わず、同じ種類のすべての通知に適用されます。

## <a name="to-specify-a-standard-notification-limit-for-each-notification-type"></a>通知の種類ごとに標準の通知の制限を指定するには

1.  コンソール ツリーで、**[ファイル サーバー リソース マネージャー]** を右クリックし、**[オプションの構成]** をクリックします。 [**ファイル サーバー リソース マネージャーのオプション**] ダイアログ ボックスが開きます。

2.  **[通知の制限]** タブで、表示されているそれぞれの通知の種類に対して、分単位で値を入力します。

3.  **[OK]** をクリックします。

> [!Note]
> 特定のクォータまたはファイル スクリーンの通知に関連付けられている時間制限をカスタマイズするには、[ファイル サーバー リソース マネージャー](/powershell/module/fileserverresourcemanager/)のコマンド ライン ツールである **Dirquota.exe** と **Filescrn.exe** を使用できます。

## <a name="additional-references"></a>その他の参照情報

-   [ファイル サーバー リソース マネージャーのオプションを設定する](setting-file-server-resource-manager-options.md)
-   [コマンドライン ツール](command-line-tools.md)
