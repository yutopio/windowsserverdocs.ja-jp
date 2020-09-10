---
title: 削除 DriverGroupPackage
description: 削除 DriverGroupPackage に関するリファレンス記事。サーバー上のドライバーグループからドライバーパッケージを削除します。
ms.topic: reference
ms.assetid: 2e48616d-d6a4-45f0-a5c6-efe62bf6a0ed
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2cddeca84ba4993d8d77a4b55062d6ba4255abf9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635066"
---
# <a name="remove-drivergrouppackage"></a>削除 DriverGroupPackage



サーバー上のドライバー グループからドライバー パッケージを削除します。

## <a name="syntax"></a>構文

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:<Group Name> [/Server:<Server Name>] {/DriverPackage:<Name> | /PackageId:<ID>}
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|[/Server:\<Server name>]|サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。|
|[/DriverPackage:\<Name>]|削除するドライバー パッケージの名前を指定します。|
|[/パッケージ Id:\<ID>]|削除するドライバー パッケージの Windows 展開サービス ID を指定します。 ドライバー パッケージを名前によって一意に識別できない場合は、このオプションを指定する必要があります。|

## <a name="examples"></a>例

```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318}
```
```
WDSUTIL /Remove-DriverGroupPackage /DriverGroup:PrinterDrivers /DriverPackage:XYZ
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)