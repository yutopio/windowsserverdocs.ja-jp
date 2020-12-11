---
description: '詳細情報: ヘルプデスクへのリンクの追加'
ms.assetid: 2bac7744-9de3-491a-b0a2-4e843cec7344
title: ヘルプ デスク リンクの追加
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: c806390687d5293feacd2575b10569504334914f
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97044370"
---
# <a name="add-help-desk-link"></a>ヘルプ デスク リンクの追加


## <a name="to-add-a-help-desk-link"></a>ヘルプデスクのリンクを追加するには
サインインページに表示されるヘルプデスクリンクを追加するには、 \- 次の Windows PowerShell コマンドレットと構文を使用します。

![ヘルプデスクの追加](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)


`Set-AdfsGlobalWebContent -HelpDeskLink https://fs1.contoso.com/help/ -HelpDeskLinkText Help`


> [!IMPORTANT]
> このコマンドレットの `linkText` パラメーターは、既定値である *Help* を使用する場合は必要ありません。 既定値には、すべてのクライアント ロケールでローカライズ済みであるという利点があります。 ページをカスタマイズすると、カスタマイズ設定が優先されるため、サポートするすべての言語でページをカスタマイズする必要があります。


## <a name="additional-references"></a>その他のリファレンス
[AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)
