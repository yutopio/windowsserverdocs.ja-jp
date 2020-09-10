---
title: サブコマンドの停止-サーバー
description: サブコマンドの参照記事。 Windows 展開サービスサーバー上のすべてのサービスを停止します。
ms.topic: reference
ms.assetid: 09f411c0-099f-4591-95fd-b77b3fd9118a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c84b95607b4cf0fb69765dbc941d7e984e43d7cf
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626843"
---
# <a name="subcommand-stop-server"></a>サブコマンド: 停止サーバー

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービス サーバー上のすべてのサービスを停止します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Stop-Server [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|Description|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サービスを停止するには、次のいずれかを入力します。
```
wdsutil /Stop-Server
wdsutil /verbose /Stop-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[サーバーの無効化コマンド](using-the-disable-server-command.md) 
 の使用[Enable Server コマンド](using-the-enable-server-command.md) 
 の使用[Get Server コマンド](using-the-get-server-command.md) 
 の使用[Initialize-Server コマンド](using-the-initialize-server-command.md) 
 の使用[サブコマンド: サーバー](subcommand-set-server.md) 
 の設定[サブコマンド: start-Server](subcommand-start-server.md) 
[初期化解除サーバーオプション](the-uninitialize-server-option.md)
