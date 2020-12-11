---
description: '詳細情報: AD FS サインインページで会社のロゴを変更する'
ms.assetid: f7f6bac2-1100-4b00-a248-4ca3eb3cdbe9
title: AD FS サインインページで会社のロゴを変更する
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/08/2017
ms.topic: article
ms.openlocfilehash: a04f7a81c26dea4234fbb92edc44125ae11e51f6
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97040280"
---
# <a name="changing-the-company-logo-on-the-ad-fs-sign-in-page"></a>AD FS サインインページで会社のロゴを変更する

## <a name="change-company-logo"></a>会社ロゴの変更

サインインページに表示される会社のロゴを変更するには \- 、次の Powershell Windows powershell コマンドレットと構文を使用します。

![ロゴの変更](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom2.png)

> [!IMPORTANT]
> ロゴの寸法は 260x35 ピクセル (96 DPI) に設定して、ファイル サイズは 10 KB 以下にすることをお勧めします。

```powershell
Set-AdfsWebTheme -TargetName default -Logo @{path="c:\Contoso\logo.png"}
```

> [!NOTE]
> `TargetName` パラメーターは必須です。 AD FS と共にリリースされる既定のテーマには、 *default* という名前が付けられます。

## <a name="additional-references"></a>その他のリファレンス

[AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)
