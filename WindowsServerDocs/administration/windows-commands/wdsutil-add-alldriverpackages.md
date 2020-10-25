---
title: wdsutil 追加-alldriverpackages
description: フォルダーに格納されているすべてのドライバーパッケージをサーバーに追加する、wdsutil add alldriverpackages コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: ba6641c1-d7e9-43a9-9819-702dad5484ed
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 07d958fb382f040db34f486a28fed4b924ce45d8
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524657"
---
# <a name="wdsutil-add-alldriverpackages"></a>wdsutil 追加-alldriverpackages

サーバーにフォルダーに格納されているすべてのドライバー パッケージを追加します。

## <a name="syntax"></a>構文

```
wdsutil /Add-AllDriverPackages /FolderPath:<folderpath> [/Server:<servername>] [/Architecture:{x86 | ia64 | x64}] [/DriverGroup:<groupname>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| FolderPath`<folderpath>` | ドライバ パッケージの .inf ファイルを含むフォルダーへの完全パスを指定します。 |
| [/Server:`<servername>`] | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| [/アーキテクチャ: `{x86|ia64|x64}` ] | ドライバーパッケージのアーキテクチャの種類を指定します。 |
| [/DriverGroup:`<groupname>`] | パッケージの追加先となるドライバー グループの名前を指定します。 |

## <a name="examples"></a>例

ドライバーパッケージを追加するには、次のいずれかを入力します。

```
wdsutil /verbose /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers /Architecture:x86
```

```
wdsutil /Add-AllDriverPackages /FolderPath:C:\Temp\Drivers\Printers /DriverGroup:Printer Drivers
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)

- [追加-WdsDriverPackage](/powershell/module/wds/add-wdsdriverpackage)
