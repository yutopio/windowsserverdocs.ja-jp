---
title: wdsutil delete-autoadddevices
description: 自動追加データベースから保留、拒否、または承認されているコンピューターを削除する、wdsutil delete-autoadddevices コマンドの参照記事です。
ms.topic: reference
ms.assetid: 8dcaca6a-212e-4c36-98e3-00938eef6b9c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 610b57c7db49c5d8cf354502634cf82212d52c19
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524817"
---
# <a name="wdsutil-delete-autoadddevices"></a>wdsutil delete-autoadddevices

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

自動追加データベースから保留、拒否、または承認されているコンピューターを削除します。 このデータベースは、サーバーでこれらのコンピューターに関する情報を格納します。

## <a name="syntax"></a>構文

```
wdsutil /delete-AutoaddDevices [/Server:<Servername>] /Devicetype:{PendingDevices | RejectedDevices |ApprovedDevices}
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。 |
| (Devicetype`{PendingDevices|RejectedDevices|ApprovedDevices}` | データベースから削除するコンピューターの種類を指定します。 この種類は、 **Pendingdevices**です。これにより、状態が Pending、 **RejectedDevices**のデータベース内のすべてのコンピューターが返されます。この場合、[拒否] の状態にあるデータベース内のすべてのコンピューターが返されます **。または、[** 承認済み] の状態にあるすべてのコンピューターが返されます。 |

## <a name="examples"></a>例

すべての拒否されたコンピューターを削除するには、次のように入力します。

```
wdsutil /delete-AutoaddDevices /Devicetype:RejectedDevices
```

すべての承認されたコンピューターを削除するには、次のように入力します。

```
wdsutil /verbose /delete-AutoaddDevices /Server:MyWDSServer /Devicetype:ApprovedDevices
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil 承認-autoadddevices コマンド](wdsutil-approve-autoadddevices.md)

- [wdsutil get-autoadddevices コマンド](wdsutil-get-autoadddevices.md)

- [wdsutil 拒否-autoadddevices コマンド](wdsutil-reject-autoadddevices.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
