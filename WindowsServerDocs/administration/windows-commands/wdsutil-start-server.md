---
title: wdsutil start-サーバー
description: サブコマンドの参照記事で、Windows 展開サービスサーバーのすべてのサービスを開始します。
ms.topic: reference
ms.assetid: 1e4343e2-0a16-4e65-8769-c09adaef5680
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 03791bd3a313f1ab2a5a2e076036d0aaddb18a8e
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731366"
---
# <a name="wdsutil-start-server"></a>wdsutil start-サーバー

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービス サーバーのすべてのサービスを開始します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /start-Server [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|起動するサーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サーバーを起動するには、次のいずれかを入力します。
```
wdsutil /start-Server
wdsutil /verbose /start-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil disable-サーバーコマンド](wdsutil-disable-server.md)
- [wdsutil enable-サーバーコマンド](wdsutil-enable-server.md)
- [wdsutil get サーバーコマンド](wdsutil-get-server.md)
- [wdsutil initialize-サーバーコマンド](wdsutil-initialize-server.md)
- [wdsutil set-サーバーコマンド](wdsutil-set-server.md)
- [wdsutil stop-サーバーコマンド](wdsutil-stop-server.md)
- [wdsutil start-サーバーコマンド](wdsutil-start-server.md)
- [wdsutil 初期化解除-サーバーコマンド](wdsutil-uninitialize-server.md)
