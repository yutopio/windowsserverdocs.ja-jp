---
title: wdsutil start-transportserver
description: サブコマンドの参照記事、トランスポートサーバーのすべてのサービスを開始する、サブコマンドの開始 TransportServer です。
ms.topic: reference
ms.assetid: 0e93bc84-5b9e-4f9d-8cf0-1634417da0f6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3aa948fb86b1b69448ac131c6894ff0c41f548e8
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731385"
---
# <a name="wdsutil-start-transportserver"></a>wdsutil start-transportserver

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

トランスポート サーバーのすべてのサービスを開始します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /start-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|トランスポート サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サーバーを起動するには、次のいずれかを入力します。
```
wdsutil /start-TransportServer
wdsutil /verbose /start-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil disable-transportserver コマンド](wdsutil-disable-transportserver.md)
- [wdsutil enable transportserver コマンド](wdsutil-enable-transportserver.md)
- [wdsutil get transportserver コマンド](wdsutil-get-transportserver.md)
- [wdsutil set transportserver コマンド](wdsutil-set-transportserver.md)
- [wdsutil stop transportserver コマンド](wdsutil-stop-transportserver.md)
