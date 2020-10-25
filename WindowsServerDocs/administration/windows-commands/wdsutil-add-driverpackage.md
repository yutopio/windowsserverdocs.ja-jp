---
title: 追加 DriverPackage
description: ドライバーパッケージをサーバーに追加する、DriverPackage コマンドの参照記事です。
ms.topic: reference
ms.assetid: 3ac9e8d5-63ec-4ce8-86fc-85d28011050b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c85279cc160ca12b52f4cf7225d0ac41700973bc
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524526"
---
# <a name="add-driverpackage"></a>追加 DriverPackage

ドライバー パッケージをサーバーに追加します。

## <a name="syntax"></a>構文

```
wdsutil /Add-DriverPackage /InfFile:<Inf File path> [/Server:<Server name>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<Group Name>] [/Name:<Friendly Name>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /InfFile:`<InfFilepath>` | 追加する .inf ファイルの完全なパスを指定します。 |
| [/Server:`<Servername>`] | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| [/アーキテクチャ: `{x86 | ia64 | x64}` ] | ドライバーパッケージのアーキテクチャの種類を指定します。 |
| [/DriverGroup:`<groupname>`] | パッケージの追加先となるドライバー グループの名前を指定します。 |
| [/Name:`<friendlyname>`] | ドライバーパッケージのフレンドリ名を指定します。 |

## <a name="examples"></a>例

ドライバーパッケージを追加するには、次のいずれかを入力します。

```
wdsutil /verbose /Add-DriverPackage /InfFile:C:\Temp\Display.inf
```

```
wdsutil /Add-DriverPackage /Server:MyWDSServer /InfFile:C:\Temp\Display.inf /Architecture:x86 /DriverGroup:x86Drivers /Name:Display Driver
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil add drivergrouppackage コマンド](wdsutil-add-drivergrouppackage.md)

- [wdsutil add alldriverpackages コマンド](wdsutil-add-alldriverpackages.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
