---
title: get TransportServer
description: 指定されたトランスポートサーバーに関する情報を表示する、TransportServer のリファレンス記事です。
ms.topic: reference
ms.assetid: de634123-0179-41b2-9c6f-726508130ff5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 27419bac432dc59ecaa64a6966830528293a4a12
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640071"
---
# <a name="get-transportserver"></a>get TransportServer

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定したトランスポート サーバーの情報を表示します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Get-TransportServer [/Server:<Server name>] /Show:{Config}
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|/表示: {Config}|指定したトランスポート サーバーの構成情報を返します。|
## <a name="examples"></a>例
サーバーに関する情報を表示するには、次のように入力します。
```
wdsutil /Get-TransportServer /Show:Config
```
構成情報を表示するには、次のように入力します。
```
wdsutil /Get-TransportServer /Server:MyWDSServer /Show:Config
```
## <a name="additional-references"></a>その他の参照情報
- [コマンドライン構文のキー](command-line-syntax-key.md) 
[無効化-TransportServer コマンド](using-the-disable-transportserver-command.md) 
 の使用[Enable TransportServer コマンド](using-the-enable-transportserver-command.md) 
 の使用[サブコマンド: Set TransportServer](subcommand-set-transportserver.md) 
[サブコマンド: 開始 TransportServer](subcommand-start-transportserver.md) 
[サブコマンド: 停止 TransportServer](subcommand-stop-transportserver.md)
