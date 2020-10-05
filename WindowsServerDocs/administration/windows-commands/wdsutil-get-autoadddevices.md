---
title: wdsutil get-autoadddevices
description: Windows 展開サービスサーバー上の自動追加データベースにあるすべてのコンピューターを表示する、wdsutil get autoadddevices のリファレンス記事です。
ms.topic: reference
ms.assetid: 24b4b688-55b0-4bd9-a2f5-7ef4b3dfe2f2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c7d5be85ce29a41714d70d8bdfa11e3afa1661d6
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730857"
---
# <a name="wdsutil-get-autoadddevices"></a>wdsutil get-autoadddevices

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービスサーバー上の自動追加データベースにあるすべてのコンピューターを表示します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Get-AutoaddDevices [/Server:<Server name>] /Devicetype:{PendingDevices | RejectedDevices | ApprovedDevices}
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
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
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil delete-autoadddevices コマンド](wdsutil-delete-autoadddevices.md)
- [wdsutil 承認-autoadddevices コマンド](wdsutil-approve-autoadddevices.md)
- [wdsutil 拒否-autoadddevices コマンド](wdsutil-reject-autoadddevices.md)
