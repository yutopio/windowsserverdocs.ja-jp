---
title: 追加 DriverPackage
description: ドライバーパッケージをサーバーに追加する追加 DriverPackage のリファレンス記事です。
ms.topic: reference
ms.assetid: 3ac9e8d5-63ec-4ce8-86fc-85d28011050b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0a1876727d4d79cf4ce3c86c654a9be0b7c6795d
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029850"
---
# <a name="add-driverpackage"></a>追加 DriverPackage

ドライバー パッケージをサーバーに追加します。

## <a name="syntax"></a>構文

```
WDSUTIL /Add-DriverPackage /InfFile:<Inf File path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>] [/Name:<Friendly Name>]
```

### <a name="parameters"></a>パラメーター

|          パラメーター           |                                                              説明                                                              |
|------------------------------|---------------------------------------------------------------------------------------------------------------------------------------|
|   InfFile:\<Inf File path>   |                                           追加する .inf ファイルの完全なパスを指定します。                                            |
|    Server\<Server name>    | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
|      /アーキテクチャ: {x86      |                                                                 ia64                                                                  |
| [/DriverGroup:\<Group Name>] |                             パッケージの追加先となるドライバー グループの名前を指定します。                              |
|   [/Name:\<Friendly Name>]   |                                           ドライバー パッケージのフレンドリ名を示しています。                                            |

## <a name="examples"></a>例

ドライバー パッケージを追加するには、次のいずれかを入力します。
```
WDSUTIL /verbose /Add-DriverPackage /InfFile:C:\Temp\Display.inf
```
```
WDSUTIL /Add-DriverPackage /Server:MyWDSServer /InfFile:C:\Temp\Display.inf /Architecture:x86 /DriverGroup:x86Drivers /Name:Display Driver
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

