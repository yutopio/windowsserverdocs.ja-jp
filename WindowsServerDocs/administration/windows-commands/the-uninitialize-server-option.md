---
title: 初期化解除-サーバー
description: 初期サーバー構成中にサーバーに加えられた変更を元に戻すサーバーの初期化解除に関するリファレンス記事です。
ms.topic: reference
ms.assetid: 015efb04-fe84-469f-bd81-49d0046296b2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: da747dd06ca9621e4261edc436eea48fb2a3917f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640476"
---
# <a name="uninitialize-server"></a>初期化解除-サーバー

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバーの初期構成中に、サーバーに加えられた変更を元に戻します。 これには、 **サーバー** オプションまたは Windows 展開サービス mmc スナップインのいずれかによって行われた変更が含まれます。 このコマンドは、サーバーを未構成の状態にリセットしていることに注意してください。 このコマンドでは、remoteInstall 共有フォルダーの内容は変更されません。 代わりに、サーバーを再初期化できるように、サーバーの状態をリセットします。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Uninitialize-Server [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サーバーを再初期化するには、次のいずれかを入力します。
```
wdsutil /Uninitialize-Server
wdsutil /verbose /Uninitialize-Server /Server:MyWDSServer
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[サーバーの無効化コマンド](using-the-disable-server-command.md) 
 の使用[Enable Server コマンド](using-the-enable-server-command.md) 
 の使用[Get Server コマンド](using-the-get-server-command.md) 
 の使用[Initialize-Server コマンド](using-the-initialize-server-command.md) 
 の使用[サブコマンド: サーバー](subcommand-set-server.md) 
 の設定[サブコマンド: start-Server](subcommand-start-server.md) 
[サブコマンド: サーバーの停止](subcommand-stop-server.md)
