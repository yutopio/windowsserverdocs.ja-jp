---
title: wdsutil 拒否-autoadddevices
description: Wdsutil reject-autoadddevices の参照記事。管理者の承認が保留中のコンピューターを拒否します。
ms.topic: reference
ms.assetid: ea25a4b2-5fad-4360-9c47-c2c9df7ea31f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2cb970ce6b51933e72f208f6fbcc50bcb7b3164b
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730690"
---
# <a name="wdsutil-reject-autoadddevices"></a>wdsutil 拒否-autoadddevices

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

管理者の承認が保留中のコンピューターを拒否します。 自動追加ポリシーを有効にすると、不明なコンピューター (事前登録されていないコンピューター) がイメージをインストールする前に、管理者の承認が必要になります。 このポリシーを有効にするには、[サーバーのプロパティ] ページの [ **PXE 応答** ] タブを使用します。
## <a name="syntax"></a>構文
```
wdsutil [Options] /Reject-AutoaddDevices [/Server:<Server name>] /RequestId:<Request ID or ALL>
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|/RequestId: < 要求 ID と #124 文字です。すべて >|保留中のコンピューターに割り当てられた要求 ID を指定します。 保留中のすべてのコンピューターを拒否するには指定 **すべて**です。|
## <a name="examples"></a>例
1 台のコンピューターを拒否するには、次のように入力します。
```
wdsutil /Reject-AutoaddDevices /RequestId:12
```
すべてのコンピューターを拒否するには、次のように入力します。
```
wdsutil /verbose /Reject-AutoaddDevices /Server:MyWDSServer /RequestId:ALL
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil 承認-autoadddevices コマンド](wdsutil-approve-autoadddevices.md)
- [wdsutil delete-autoadddevices コマンド](wdsutil-delete-autoadddevices.md)
- [wdsutil get-autoadddevices コマンド](wdsutil-get-autoadddevices.md)
