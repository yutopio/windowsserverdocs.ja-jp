---
description: 詳細については、AD FS でのカスタム Web テーマに関するページを参照してください。
ms.assetid: 0379abc3-25c7-46ab-9a6b-80a5152365b0
title: AD FS でのカスタム Web テーマ
author: billmath
ms.author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 303d1903be5a21d35abe2724401d73170673751c
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97039940"
---
# <a name="custom-web-themes-in-ad-fs"></a>AD FS でのカスタム Web テーマ

\- \- 既定と呼ばれるのは、そのまま出荷されるテーマです \- 。 既定のテーマをエクスポートして使用すると、カスタマイズを簡単に開始できます。 カスタマイズできるのは外観と動作です。.css ファイルを変更してレイアウトを調整し、変更済みの新しいテーマをインポートして適用すると、カスタマイズされた外観と動作を使用できるようになります。 .css ファイルを使用することで、Web デザイナーとの共同作業も容易になります。

次のコマンドレットを実行すると、既定の Web テーマを複製してカスタム Web テーマが作成されます。

```powershell
New-AdfsWebTheme –Name custom –SourceName default
```

既存の .css ファイルを変更したり、新しい .css ファイルを使用して新しい Web テーマを構成したりできます。 Web テーマをエクスポートするには、次のコマンドレットを使用します。

```powershell
Export-AdfsWebTheme –Name default –DirectoryPath c:\theme
```

.css ファイルを新しいテーマに適用するには、次のコマンドレットを使用します。

```powershell
Set-AdfsWebTheme –TargetName custom –StyleSheet @{path="c:\NewTheme.css"}
```

新しいスタイル シートからカスタム Web テーマを作成するには、次のコマンドレットを使用します。

```powershell
New-AdfsWebTheme –Name custom –StyleSheet @{path="c:\NewTheme.css"} –RTLStyleSheetPath c:\NewRtlTheme.css
```

AD FS にカスタム web テーマを適用するには、次のコマンドレットを使用します。

```powershell
Set-AdfsWebConfig -ActiveThemeName custom
```

JavaScript を AD FS に追加するには、次のコマンドレットを使用します。

```powershell
Set-AdfsWebTheme -TargetName custom -AdditionalFileResource @{Uri=' /adfs/portal/script/onload.js';path="D:\inetpub\adfsassets\script\onload.js"}
```

## <a name="additional-references"></a>その他のリファレンス

[AD FS ユーザーサインインのカスタマイズ](AD-FS-user-sign-in-customization.md)
