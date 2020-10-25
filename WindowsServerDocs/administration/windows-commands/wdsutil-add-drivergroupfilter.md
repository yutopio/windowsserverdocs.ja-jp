---
title: 追加 DriverGroupFilter
description: Add DriverGroupFilter コマンドのリファレンス記事。サーバー上のドライバーグループにフィルターを追加します。
ms.topic: reference
ms.assetid: a66c5e68-99ea-4e47-b68d-8109633ae336
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: bd9e26e7bdf6b1a03d01b2993c969bbbcf5b8754
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524607"
---
# <a name="add-drivergroupfilter"></a>追加 DriverGroupFilter

サーバー上のドライバー グループにフィルターを追加します。

## <a name="syntax"></a>構文

```
wdsutil /Add-DriverGroupFilter /DriverGroup:<Group Name> [/Server:<Server name>] /FilterType:<Filter Type> /Policy:{Include | Exclude} /Value:<Value> [/Value:<Value> ...]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| DriverGroup`<Groupname>` | 新しいドライバー グループの名前を指定します。 |
| Server`<Servername>` | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| Filtertype`<Filtertype>` | グループに追加するフィルターの種類を指定します。 1 つのコマンドでは、複数のフィルターの種類を指定できます。 各フィルターの種類は続けてください **/policy:enabled** と 1 つ以上 **/value**します。 有効な値は、次のとおりです。<ul><li>BiosVendor</li><li>Bios のバージョン</li><li>Chassistype</li><li>Manufacturer</li><li>Uuid</li><li>Osversion</li><li>Osedition</li><li>OsLanguage</li></ul> 他のすべてのフィルターの種類の値を取得する方法については、「 [ドライバーグループのフィルター](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759191(v=ws.11))」を参照してください。 |
| [/ポリシー: `{Include|Exclude}` ] | フィルターを設定するポリシーを指定します。 場合 **/policy:enabled** に設定されている **Include**, 、フィルターに一致するクライアント コンピューターがこのグループのドライバーをインストールを許可します。 場合 **/policy:enabled** に設定されている **除外**, 、このグループのドライバーをインストールするフィルターに一致するクライアント コンピューターは許可されません。 |
| [/Value:`<Value>`] | **/Filtertype**に対応するクライアントの値を指定します。 1 つの型に複数の値を指定できます。 許容されるフィルターの種類の値については、「 [ドライバーグループのフィルター](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759191(v=ws.11))」を参照してください。 |

## <a name="examples"></a>例

ドライバーグループにフィルターを追加するには、次のいずれかを入力します。

```
wdsutil /Add-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /Value:Name1 /Value:Name2
```

```
wdsutil /Add-DriverGroupFilter /DriverGroup:PrinterDrivers /FilterType:Manufacturer /Policy:Include /Value:Name1 /FilterType:ChassisType /Policy:Exclude /Value:Tower /Value:MiniTower
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil add drivergrouppackage コマンド](wdsutil-add-drivergrouppackage.md)

- [wdsutil add drivergrouppackages コマンド](wdsutil-add-drivergrouppackages.md)

- [wdsutil add drivergroup コマンド](wdsutil-add-drivergroup.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
