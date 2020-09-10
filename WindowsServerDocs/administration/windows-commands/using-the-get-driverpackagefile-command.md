---
title: get DriverPackageFile
description: ドライバーパッケージについての情報を表示する get DriverPackageFile の参照記事。ドライバーパッケージに含まれるドライバーとファイルを含みます。
ms.topic: reference
ms.assetid: f01a2c67-7e9c-4aad-b625-383f5a1fca25
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9ab52e1040651398d4789ea51ef9b6dc40dc6d54
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624625"
---
# <a name="get-driverpackagefile"></a>get DriverPackageFile

ドライバーが含まれているファイルを含むドライバー パッケージについての情報を表示します。

## <a name="syntax"></a>構文

```
WDSUTIL /Get-DriverPackageFile /InfFile:<Inf File path> [/Architecture:{x86 | ia64 | x64}] [/Show:{Drivers | Files | All}]
```

### <a name="parameters"></a>パラメーター

|         パラメーター         |                              Description                               |
|---------------------------|------------------------------------------------------------------------|
| /InfFile:\<Inf File path> | ドライバー パッケージの .inf ファイルの完全パスとファイル名を指定します。 |
|    [/アーキテクチャ: {x86    |                                  ia64                                  |
|     [/Show: {Drivers      |                                 Files                                  |

## <a name="examples"></a>例

ドライバー ファイルに関する情報を表示するには、次のように入力します。
```
WDSUTIL /Get-DriverPackageFile /InfFile:C:\temp\1394.inf /Architecture:x86
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)