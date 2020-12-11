---
description: 詳細については、「ホームリンクの追加」を参照してください。
ms.assetid: da035189-e87f-4597-9933-49bf391a8d5d
title: ホーム リンクの追加
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 5f684ae3e68459721678a50c91cc04d58c89d81c
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97039350"
---
# <a name="add-home-link"></a>ホーム リンクの追加

サインインページに表示されるホームリンクを追加するには、 \- 次の Windows PowerShell コマンドレットと構文を使用します。


![ホームリンクの追加](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)


`Set-AdfsGlobalWebContent -HomeLink https://fs1.contoso.com/home/ -HomeLinkText Home `


> [!IMPORTANT]
> このコマンドレットの `linkText` パラメーターは、既定値である *Home* を使用する場合は必要ありません。 既定値には、すべてのクライアント ロケールでローカライズ済みであるという利点があります。 サインインページをカスタマイズすると、 \- カスタマイズが優先されるため、サポートするすべての言語に合わせてカスタマイズする必要があります。

## <a name="additional-references"></a>その他のリファレンス
[AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)
