---
description: '詳細情報: プライバシーリンクの追加'
ms.assetid: 1ca6f87f-7272-4767-b609-3e295ac7d32f
title: プライバシー リンクの追加
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: c15491ed9540c68c76e9a6ddfbcdf830690c9dc1
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97044310"
---
# <a name="add-privacy-link"></a>プライバシー リンクの追加


サインインページに表示されるプライバシーリンクを追加するには、 \- 次の Windows PowerShell コマンドレットと構文を使用します。

![プライバシーリンクの追加](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)


`Set-AdfsGlobalWebContent -PrivacyLink https://fs1.contoso.com/privacy/ -PrivacyLinkText Privacy`


> [!IMPORTANT]
> このコマンドレットの `linkText` パラメーターは、既定値である *Privacy* を使用する場合は必要ありません。 既定値には、すべてのクライアント ロケールでページがローカライズ済みであるという利点があります。 サインインページをカスタマイズすると、 \- カスタマイズが優先されるため、サポートするすべての言語に合わせてカスタマイズする必要があります。 すべてのカスタマイズ コンテンツには、ロケール パラメーターが設定されます。 ローカライズされたコンテンツを構成する場合は、最初に "en" などの国のロケールを使用しないように構成して \- から、国と地域 \- に固有のロケール ("en-us" など) を構成する必要があり \- ます。

## <a name="additional-references"></a>その他のリファレンス
[AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)
