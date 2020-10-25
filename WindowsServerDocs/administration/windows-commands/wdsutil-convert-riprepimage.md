---
title: riprepimage
description: 既存のリモートインストール準備 (RIPrep) イメージを Windows イメージ (.wim) 形式に変換する riprepimage コマンドの参照記事。
ms.topic: reference
ms.assetid: 88c2b96f-5947-4b64-9dcf-1946b3c013cf
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4062aa747bd02956a498c16c9e8aa15e96d8170d
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524927"
---
# <a name="convert-riprepimage"></a>riprepimage

既存のリモート インストールの準備 (RIPrep) イメージを Windows イメージ (.wim) 形式に変換します。

## <a name="syntax"></a>構文

```
wdsutil [Options] /Convert-RIPrepImage /FilePath:<Filepath and name> /DestinationImage /FilePath:<Filepath and name> [/Name:<Name>] [/Description:<Description>] [/InPlace] [/Overwrite:{Yes | No | Append}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| FilePath`<Filepath and name>` | RIPrep イメージに対応する .sif ファイルの完全なファイルパスと名前を指定します。 このファイルは通常、Riprep と呼ばれ、RIPrep イメージを含むフォルダーの **\ Templates** サブフォルダーにあります。 |
| /DestinationImage | コピー先の画像の設定を指定します。  では、次のオプションを使用します。<ul><li>`/FilePath:<Filepath and name>` -新しいファイルの完全なファイルパスを設定します。 例: **C:\Temp\convert.wim**</li><li>[ `/Name:<Name>` ]-イメージの表示名を設定します。 表示名が指定されていない場合は、ソースイメージの表示名が使用されます。</li><li>[ `/Description:<Description>` ]-イメージの説明を設定します。</li><li>[/インプレース]-変換が元の RIPrep イメージで実行され、元のイメージのコピーでは実行されないことを指定します。これは既定の動作です。</li><li>[ `/Overwrite:{Yes | No | Append}` -このイメージが既存のファイルを上書きするか追加するかを設定します。</li></ul> |

## <a name="examples"></a>例

指定した RIPrep.sif イメージを RIPREP.wim に変換するには、次のように入力します。

```
wdsutil /Convert-RiPrepImage /FilePath:R:\RemoteInstall\Setup\English \Images\Win2k3.SP1\i386\Templates\riprep.sif /DestinationImage /FilePath:C:\Temp\RIPREP.wim
```

RIPREP.wim を指定した名前と説明した、指定された RIPrep.sif イメージに変換をファイルが既に存在する場合、新しいファイルで上書きは、次のように入力します。

```
wdsutil /Verbose /Progress /Convert-RiPrepImage /FilePath:\\Server \RemInst\Setup\English\Images\WinXP.SP2\i386\Templates\riprep.sif /DestinationImage /FilePath:\\Server\Share\RIPREP.wim /Name:WindowsXP image /Description:Converted RIPREP image of WindowsXP /Overwrite:Append
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
