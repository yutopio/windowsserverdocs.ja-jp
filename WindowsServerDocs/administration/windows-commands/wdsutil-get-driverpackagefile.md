---
title: wdsutil get driverpackagefile
description: Wdsutil get driverpackagefile のリファレンス記事。ドライバーパッケージについての情報を表示します。これには、ドライバーパッケージに含まれるドライバーとファイルも含まれます。
ms.topic: reference
ms.assetid: f01a2c67-7e9c-4aad-b625-383f5a1fca25
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 900fc109c52908870733d4892e6d70f4a7b84c07
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524267"
---
# <a name="wdsutil-get-driverpackagefile"></a>wdsutil get driverpackagefile

ドライバーが含まれているファイルを含むドライバー パッケージについての情報を表示します。

## <a name="syntax"></a>構文

```
wdsutil /Get-DriverPackageFile /InfFile:<Inf File path> [/Architecture:{x86 | ia64 | x64}] [/Show:{Drivers | Files | All}]
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
wdsutil /Get-DriverPackageFile /InfFile:C:\temp\1394.inf /Architecture:x86
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)