---
title: wdsutil add drivergrouppackage
description: ドライバーパッケージをドライバーグループに追加する、wdsutil add drivergrouppackage コマンドの参照記事です。
ms.topic: reference
ms.assetid: 7cd323ae-9049-448e-a460-6c7d6462d4c8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4bf7b7c6cae4551e09fa5aa7d0244e5e4f0407e4
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524547"
---
# <a name="wdsutil-add-drivergrouppackage"></a>wdsutil add drivergrouppackage

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ドライバー パッケージをドライバー グループに追加します。

## <a name="syntax"></a>構文

```
wdsutil /add-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| DriverGroup`<Groupname>` | 新しいドライバー グループの名前を指定します。 |
| Server`<Servername>` | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| DriverPackage`<Name>` | グループに追加するドライバー パッケージの名前を指定します。 ドライバー パッケージを名前によって一意に識別できない場合は、このオプションを指定する必要があります。 |
| PackageId`<ID>` | パッケージの ID を指定します。 パッケージ ID を検索するには、パッケージが含まれているドライバーグループ (または [ **すべてのパッケージ** ] ノード) を選択し、パッケージを右クリックして、[ **プロパティ**] を選択します。 パッケージ ID が [ **全般** ] タブに表示されます。例: **{DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}**。 |

## <a name="examples"></a>例

ドライバーグループパッケージを追加するには、次のいずれかを入力します。

```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```

```
wdsutil /add-DriverGroupPackage /DriverGroup:printerdrivers /DriverPackage:XYZ
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil add drivergroupfilter コマンド](wdsutil-add-drivergroupfilter.md)

- [wdsutil add drivergrouppackages コマンド](wdsutil-add-drivergrouppackages.md)

- [wdsutil add drivergroup コマンド](wdsutil-add-drivergroup.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
