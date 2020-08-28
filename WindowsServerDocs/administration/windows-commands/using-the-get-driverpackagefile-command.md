---
title: get DriverPackageFile
description: ドライバーパッケージについての情報を表示する get DriverPackageFile の参照記事。ドライバーパッケージに含まれるドライバーとファイルを含みます。
ms.topic: reference
ms.assetid: f01a2c67-7e9c-4aad-b625-383f5a1fca25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5d1990cd307aaf5a378eaf55ac95247fe5b92405
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029660"
---
# <a name="get-driverpackagefile"></a>get DriverPackageFile

ドライバーが含まれているファイルを含むドライバー パッケージについての情報を表示します。

## <a name="syntax"></a>構文

```
WDSUTIL /Get-DriverPackageFile /InfFile:<Inf File path> [/Architecture:{x86 | ia64 | x64}] [/Show:{Drivers | Files | All}]
```

### <a name="parameters"></a>パラメーター

|         パラメーター         |                              説明                               |
|---------------------------|------------------------------------------------------------------------|
| /InfFile:\<Inf File path> | ドライバー パッケージの .inf ファイルの完全パスとファイル名を指定します。 |
|    [/アーキテクチャ: {x86    |                                  ia64                                  |
|     [/Show: {Drivers      |                                 ファイル                                  |

## <a name="examples"></a>例

ドライバー ファイルに関する情報を表示するには、次のように入力します。
```
WDSUTIL /Get-DriverPackageFile /InfFile:C:\temp\1394.inf /Architecture:x86
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)