---
title: wdsutil enable-サーバー
description: Wdsutil enable server のリファレンス記事。 Windows 展開サービスのすべてのサービスを有効にします。
ms.topic: reference
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3ec32f2bd0d269795e1f88b967804c2bb82ac9f4
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730946"
---
# <a name="wdsutil-enable-server"></a>wdsutil enable-サーバー

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービスのすべてのサービスを有効にします。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Enable-Server [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サーバー上のサービスを有効にするには、次のいずれかを実行します。
```
wdsutil /Enable-Server
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[wdsutil disable-サーバーコマンド](wdsutil-disable-server.md) 
[wdsutil Get サーバーコマンド](wdsutil-get-server.md) 
[wdsutil initialize-サーバーコマンド](wdsutil-initialize-server.md) 
[wdsutil set-サーバーコマンド](wdsutil-set-server.md) 
[wdsutil start-サーバーコマンド](wdsutil-start-server.md) 
[wdsutil stop-サーバーコマンド](wdsutil-stop-server.md) 
[wdsutil 初期化解除-サーバーコマンド](wdsutil-uninitialize-server.md)
