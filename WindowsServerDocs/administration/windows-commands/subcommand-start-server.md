---
title: サブコマンドの開始-サーバー
description: サブコマンドの参照記事で、Windows 展開サービスサーバーのすべてのサービスを開始します。
ms.topic: reference
ms.assetid: 1e4343e2-0a16-4e65-8769-c09adaef5680
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2a566116d6a584bf89a80107ca2cb78bfbdb738b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633908"
---
# <a name="subcommand-start-server"></a>サブコマンド: 開始サーバー

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
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[サーバーの無効化コマンド](using-the-disable-server-command.md) 
 の使用[Enable Server コマンド](using-the-enable-server-command.md) 
 の使用[Get Server コマンド](using-the-get-server-command.md) 
 の使用[Initialize-Server コマンド](using-the-initialize-server-command.md) 
 の使用[サブコマンド: サーバー](subcommand-set-server.md) 
 の設定[サブコマンド: サーバー](subcommand-stop-server.md) 
 の停止[初期化解除サーバーオプション](the-uninitialize-server-option.md)
