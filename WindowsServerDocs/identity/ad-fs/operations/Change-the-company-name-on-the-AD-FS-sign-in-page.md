---
description: 詳細については、AD FS サインインページで会社名を変更する
ms.assetid: 28043fc4-a34d-4710-ac3b-5c9d4d6a895c
title: AD FS サインインページで会社名を変更する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 907043517d56790cd4f6de49d67de5ed3905f0ad
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97040250"
---
# <a name="change-the-company-name-on-the-ad-fs-sign-in-page"></a>AD FS サインインページで会社名を変更する

サインインページに表示される会社の名前を変更するには、 \- 次の Windows PowerShell コマンドレットと構文を使用します。 この値には、セットアップ時に入力したフェデレーション サービスの表示名が既定で設定されています。

![名前の変更](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png)

```powershell
    Set-AdfsGlobalWebContent –CompanyName "Contoso Corp"
```

> [!NOTE]
> Windows PowerShell Integrated Scripting Environment ISE を使用して会社名を変更することもでき \( \) ます。 Windows PowerShell ISE を使用すると、Unicode 準拠の環境でコンテンツを表示でき \- ます。 詳細については、「 [Windows PowerShell ISE の紹介](/previous-versions/mt707506(v=msdn.10))」を参照してください。

## <a name="additional-references"></a>その他のリファレンス

- [AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)
