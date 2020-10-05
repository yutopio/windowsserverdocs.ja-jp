---
title: DriverGroup を削除します。
description: ドライバーグループをサーバーから削除する、削除 DriverGroup のリファレンス記事です。
ms.topic: reference
ms.assetid: 1fefe9df-9782-433c-8abe-3f1a35e50da2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 55cb50d43bf433d5421f4152053844f89d45f379
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730698"
---
# <a name="remove-drivergroup"></a>DriverGroup を削除します。

サーバーからドライバー グループを削除します。

## <a name="syntax"></a>構文

```
WDSUTIL /Remove-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|DriverGroup\<Group Name>|削除するドライバー グループの名前を指定します。|
|[/Server:\<Server name>]|サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。|

## <a name="examples"></a>例

ドライバー グループを削除するには、次のいずれかを入力します。
```
WDSUTIL /Remove-DriverGroup /DriverGroup:PrinterDrivers
```
```
WDSUTIL /Remove-DriverGroup /DriverGroup:PrinterDrivers /Server:MyWdsServer
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)