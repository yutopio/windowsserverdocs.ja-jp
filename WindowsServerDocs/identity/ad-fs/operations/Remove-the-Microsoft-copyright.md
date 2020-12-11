---
description: '詳細情報: Microsoft 著作権情報の削除'
ms.assetid: c89a977c-b09f-44ec-be42-41e76a6cf3ad
title: Microsoft 著作権情報を削除する
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: a5b377989315462789b9b33faf5267211c93bf8c
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97039730"
---
# <a name="remove-the-microsoft-copyright"></a>Microsoft 著作権情報を削除する



既定では、AD FS のページには Microsoft 著作権情報が含まれています。 この著作権情報をカスタマイズ済みページから削除するには、次の手順に従います。

![著作権情報の削除](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1.png)

## <a name="to-remove-the-microsoft-copyright"></a>Microsoft 著作権情報を削除するには

1. 既定のテーマに基づいてカスタム テーマを作成します。

   ```powershell
   New-AdfsWebTheme –Name custom –SourceName default
   ```

2. 出力フォルダーを指定してテーマをエクスポートします。

   ```powershell
   Export-AdfsWebTheme -Name custom -DirectoryPath C:\CustomWebTheme
   ```

3. `Style.css`出力フォルダーにあるファイルを見つけます。 前の例を使用すると、パスは次のようになります。 `C:\CustomWebTheme\Css\Style.css.`

4. メモ帳などのエディターを使用してファイルを開き `Style.css` ます。

5. `#copyright` の部分を見つけたら、次のように変更します。

   ```css
   #copyright {color:#696969; display:none;}
   ```

6. 新しいファイルに基づくカスタムテーマを作成 `Style.css` します。

   ```powershell
   Set-AdfsWebTheme -TargetName custom -StyleSheet @{locale="";path="C:\customWebTheme\css\style.css"}
   ```

7. 新しいテーマをアクティブ化します。

   ```powershell
   Set-AdfsWebConfig -ActiveThemeName custom
   ```

サインインページの下部に著作権情報が表示されなくなります。

![著作権情報の削除](media/AD-FS-user-sign-in-customization/ADFS_Blue_Custom1a.png)

## <a name="additional-references"></a>その他のリファレンス
[AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)
