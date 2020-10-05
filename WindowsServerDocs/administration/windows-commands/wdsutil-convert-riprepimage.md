---
title: RiprepImage
description: 既存のリモートインストール準備 (RIPrep) イメージを Windows イメージ (.wim) 形式に変換する RiprepImage のリファレンス記事です。
ms.topic: reference
ms.assetid: 88c2b96f-5947-4b64-9dcf-1946b3c013cf
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d9f29d4409389feb862278539105b10c54629bc9
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731018"
---
# <a name="convert-riprepimage"></a>RiprepImage

既存のリモート インストールの準備 (RIPrep) イメージを Windows イメージ (.wim) 形式に変換します。

## <a name="syntax"></a>構文

```
WDSUTIL [Options] /Convert-RIPrepImage /FilePath:<File path and name>
     /DestinationImage
         /FilePath:<File path and name>
         [/Name:<Name>]
         [/Description:<Description>]
         [/InPlace]
         [/Overwrite:{Yes | No | Append}]
```

### <a name="parameters"></a>パラメーター

|            パラメーター            |                                                                                                                                                                                                                                                                                                               説明                                                                                                                                                                                                                                                                                                                |
|---------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| FilePath\<File path and name> |                                                                                                                                                                                                       RIPrep イメージに対応する .sif ファイルの完全パスとファイル名を指定します。 このファイルは、Riprep.sif と通常呼ばれるは、RIPrep イメージを含むフォルダーの \Templates サブフォルダーにあります。                                                                                                                                                                                                       |
|        /DestinationImage        | 次のオプションを使用してコピー先の画像の設定を指定します。</br>-/FilePath:\<File path and name> -新しいファイルのファイルの完全パスを設定します。 例: **C:\Temp\convert.wim**</br>-[/Name:\<Name>]-イメージの表示名を設定します。 表示名が指定されていない場合は、ソース イメージの表示名が使用されます。</br>-[/説明: \<Description>]-イメージの説明を設定します。</br>-[/InPlace] には、変換を実行して、既定の動作は、元のイメージのコピーではなくを元の RIPrep イメージを指定します。</br>-[/Overwrite: {はい |

## <a name="examples"></a>例

指定した RIPrep.sif イメージを RIPREP.wim に変換するには、次のように入力します。
```
WDSUTIL /Convert-RiPrepImage /FilePath:R:\RemoteInstall\Setup\English
\Images\Win2k3.SP1\i386\Templates\riprep.sif /DestinationImage
/FilePath:C:\Temp\RIPREP.wim
```
RIPREP.wim を指定した名前と説明した、指定された RIPrep.sif イメージに変換をファイルが既に存在する場合、新しいファイルで上書きは、次のように入力します。
```
WDSUTIL /Verbose /Progress /Convert-RiPrepImage /FilePath:\\Server
\RemInst\Setup\English\Images\WinXP.SP2\i386\Templates\riprep.sif
/DestinationImage /FilePath:\\Server\Share\RIPREP.wim
/Name:WindowsXP image /Description:Converted RIPREP image of WindowsXP
/Overwrite:Append
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)