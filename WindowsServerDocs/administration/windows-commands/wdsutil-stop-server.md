---
title: wdsutil stop-サーバー
description: サブコマンドの参照記事。 Windows 展開サービスサーバー上のすべてのサービスを停止します。
ms.topic: reference
ms.assetid: 09f411c0-099f-4591-95fd-b77b3fd9118a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0c1288900cdc5eaa46c27b6eb05fd64b9a1b16a4
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730634"
---
# <a name="wdsutil-stop-server"></a>wdsutil stop-サーバー

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービス サーバー上のすべてのサービスを停止します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Stop-Server [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サービスを停止するには、次のいずれかを入力します。
```
wdsutil /Stop-Server
wdsutil /verbose /Stop-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil disable-サーバーコマンド](wdsutil-disable-server.md)
- [wdsutil enable-サーバーコマンド](wdsutil-enable-server.md)
- [wdsutil get サーバーコマンド](wdsutil-get-server.md)
- [wdsutil initialize-サーバーコマンド](wdsutil-initialize-server.md)
- [wdsutil set-サーバーコマンド](wdsutil-set-server.md)
- [wdsutil start-サーバーコマンド](wdsutil-start-server.md)
- [wdsutil 初期化解除-サーバーコマンド](wdsutil-uninitialize-server.md)

