---
title: wdsutil enable transportserver
description: Wdsutil enable transportserver の参照記事。これにより、トランスポートサーバーのすべてのサービスが有効になります。
ms.topic: reference
ms.assetid: 9d79dba1-4b57-4a00-8cba-877e6b8618e6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4d4a294c0bda291e8340a4d8ffe54a11d487e0dd
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730945"
---
# <a name="wdsutil-enable-transportserver"></a>wdsutil enable transportserver

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

トランスポート サーバーのすべてのサービスを有効にします。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Enable-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|トランスポート サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 名前が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サーバー上のサービスを有効にするには、次のいずれかを実行します。
```
wdsutil /Enable-TransportServer
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil disable-transportserver コマンド](wdsutil-disable-transportserver.md)
- [wdsutil get transportserver コマンド](wdsutil-get-transportserver.md)
- [wdsutil set transportserver コマンド](wdsutil-set-transportserver.md)
- [wdsutil start-transportserver コマンド](wdsutil-start-transportserver.md)
- [wdsutil stop transportserver コマンド](wdsutil-stop-transportserver.md)
