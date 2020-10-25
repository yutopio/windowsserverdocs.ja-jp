---
title: DriverGroup を削除します。
description: ドライバーグループをサーバーから削除する、削除 DriverGroup のリファレンス記事です。
ms.topic: reference
ms.assetid: 1fefe9df-9782-433c-8abe-3f1a35e50da2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9bfec1636594f69ed9ea173cd2a0fcb95415296f
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524327"
---
# <a name="remove-drivergroup"></a>DriverGroup を削除します。

サーバーからドライバー グループを削除します。

## <a name="syntax"></a>構文

```
wdsutil /Remove-DriverGroup /DriverGroup:<Group Name> [/Server:<Server name>]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|DriverGroup\<Group Name>|削除するドライバー グループの名前を指定します。|
|[/Server:\<Server name>]|サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。|

## <a name="examples"></a>例

ドライバー グループを削除するには、次のいずれかを入力します。
```
wdsutil /Remove-DriverGroup /DriverGroup:PrinterDrivers
```
```
wdsutil /Remove-DriverGroup /DriverGroup:PrinterDrivers /Server:MyWdsServer
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)