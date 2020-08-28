---
title: 追加 AllDriverPackages サブコマンドを使用します。
description: フォルダーに格納されているすべてのドライバーパッケージをサーバーに追加する追加 AllDriverPackages のリファレンス記事です。
ms.topic: reference
ms.assetid: ba6641c1-d7e9-43a9-9819-702dad5484ed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ccdd132687fdc65336aeb49d317f9ccf5fbcd968
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032187"
---
# <a name="add-alldriverpackages"></a>追加-AllDriverPackages

サーバーにフォルダーに格納されているすべてのドライバー パッケージを追加します。

## <a name="syntax"></a>構文

```
WDSUTIL /Add-AllDriverPackages /FolderPath:<Folder Path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>]
```

### <a name="parameters"></a>パラメーター

|          パラメーター           |                                                              説明                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|  FolderPath\<Folder Path>  |                      ドライバ パッケージの .inf ファイルを含むフォルダーへの完全パスを指定します。                      |
|   [/Server:\<Server name>]   | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
|     [/アーキテクチャ: {x86      |                                                                 ia64                                                                  |
| [/DriverGroup:\<Group Name>] |                             パッケージの追加先となるドライバー グループの名前を指定します。                             |

## <a name="examples"></a>例

ドライバー パッケージを追加するには、次のいずれかを入力します。
```
WDSUTIL /verbose /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers /Architecture:x86
```
```
WDSUTIL /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers\Printers /DriverGroup:Printer Drivers
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

[追加-WdsDriverPackage](/previous-versions/windows/powershell-scripting/dn283440(v=wps.630))
