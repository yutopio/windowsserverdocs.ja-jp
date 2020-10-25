---
title: コピー drivergroup
description: コピー drivergroup コマンドの参照記事。このコマンドは、フィルター、ドライバーパッケージ、有効/無効の状態など、サーバー上の既存のドライバーグループを複製します。
ms.topic: reference
ms.assetid: 0aaf6fa5-8b5b-4a1e-ae9b-8b5c6d89f571
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 924f6181e424dad88a33f1421098e658275d1fa3
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524917"
---
# <a name="copy-drivergroup"></a>コピー drivergroup

フィルター、ドライバー パッケージ、および有効/無効状態を含む、サーバー上の既存のドライバー グループを複製します。

## <a name="syntax"></a>構文

```
wdsutil /Copy-DriverGroup [/Server:<Server name>] /DriverGroup:<Source Groupname> /GroupName:<New Groupname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| Server`<Servername>` | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| DriverGroup`<Source Groupname>` | ソースのドライバー グループの名前を指定します。 |
| GroupName`<New Groupname>` | 新しいドライバー グループの名前を指定します。 |

## <a name="examples"></a>例

ドライバーグループをコピーするには、次のいずれかを入力します。

```
wdsutil /Copy-DriverGroup /Server:MyWdsServer /DriverGroup:PrinterDrivers /GroupName:X86PrinterDrivers
```

```
wdsutil /Copy-DriverGroup /DriverGroup:PrinterDrivers /GroupName:ColorPrinterDrivers
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
