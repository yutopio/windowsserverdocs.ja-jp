---
title: 取得-AutoaddDevices
description: Get AutoaddDevices の参照記事。 Windows 展開サービスサーバー上の自動追加データベースにあるすべてのコンピューターが表示されます。
ms.topic: reference
ms.assetid: 24b4b688-55b0-4bd9-a2f5-7ef4b3dfe2f2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f186d36fbdc4ccfac26eae9092c8bb89973d8835
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626344"
---
# <a name="get-autoadddevices"></a>取得-AutoaddDevices

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービスサーバー上の自動追加データベースにあるすべてのコンピューターを表示します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```
### <a name="parameters"></a>パラメーター
|パラメーター|Description|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|/Devicetype: {PendingDevices &#124; RejectedDevices &#124; ApprovedDevices}|コンピューターに戻すの種類を指定します。<p>-   **Pendingdevices** は、状態が [保留中] になっているデータベース内のすべてのコンピューターを返します。<br />-   **RejectedDevices** は、データベース内の、状態が拒否のすべてのコンピューターを返します。<br />-   **ApprovedDevices** は、状態が承認済みのデータベース内のすべてのコンピューターを返します。|
## <a name="examples"></a>例
すべての承認済みのコンピューターを表示するには、次のように入力します。
```
wdsutil /Get-AutoaddDevices /Devicetype:ApprovedDevices
```
すべての拒否されたコンピューターを表示するには、次のように入力します。
```
wdsutil /verbose /Get-AutoaddDevices /Devicetype:RejectedDevices /Server:MyWDSServer
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[Delete AutoaddDevices コマンド](using-the-delete-autoadddevices-command.md) 
 の使用[承認-AutoaddDevices コマンド](using-the-approve-autoadddevices-command.md) 
 の使用[拒否 AutoaddDevices コマンドの使用](using-the-reject-autoadddevices-command.md)
