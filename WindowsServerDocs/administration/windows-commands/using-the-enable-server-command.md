---
title: サーバーを有効にする
description: Windows 展開サービスのすべてのサービスを有効にする、enable サーバーのリファレンス記事。
ms.topic: reference
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8da3985ba781b7dfbef586cf68f5f78c6f7cd17f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637629"
---
# <a name="enable-server"></a>サーバーを有効にする

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
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[サーバーの無効化コマンド](using-the-disable-server-command.md) 
 の使用[Get Server コマンド](using-the-get-server-command.md) 
 の使用[Initialize-Server コマンド](using-the-initialize-server-command.md) 
 の使用[サブコマンド: サーバー](subcommand-set-server.md) 
 の設定[サブコマンド: start-Server](subcommand-start-server.md) 
[サブコマンド: サーバー](subcommand-stop-server.md) 
 の停止[初期化解除サーバーオプション](the-uninitialize-server-option.md)
