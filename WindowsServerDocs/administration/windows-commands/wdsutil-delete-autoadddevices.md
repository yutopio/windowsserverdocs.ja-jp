---
title: wdsutil delete-autoadddevices
description: 自動追加データベースから保留、拒否、または承認されたコンピューターを削除する、wdsutil delete-autoadddevices のリファレンス記事です。
ms.topic: reference
ms.assetid: 8dcaca6a-212e-4c36-98e3-00938eef6b9c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 98c5aa38fd5394d4060cf9eba874d1be5cef845b
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730994"
---
# <a name="wdsutil-delete-autoadddevices"></a>wdsutil delete-autoadddevices

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

自動追加データベースから保留、拒否、または承認されているコンピューターを削除します。 このデータベースは、サーバーでこれらのコンピューターに関する情報を格納します。

## <a name="syntax"></a>構文
```
wdsutil /delete-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices |ApprovedDevices}
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|/Devicetype: {PendingDevices &#124; RejectedDevices &#124;ApprovedDevices}|データベースから削除するコンピューターの種類を指定します。 次の 3 種類のいずれかになります。<p>-   **Pendingdevices** は、状態が [保留中] になっているデータベース内のすべてのコンピューターを返します。<br />-   **RejectedDevices** は、データベース内の、状態が拒否のすべてのコンピューターを返します。<br />-   **ApprovedDevices** は、状態が承認済みのすべてのコンピューターを返します。|
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
