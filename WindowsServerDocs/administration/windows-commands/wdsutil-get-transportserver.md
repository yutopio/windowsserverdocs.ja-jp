---
title: wdsutil get transportserver
description: 指定されたトランスポートサーバーに関する情報を表示する wdsutil get transportserver のリファレンス記事です。
ms.topic: reference
ms.assetid: de634123-0179-41b2-9c6f-726508130ff5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a0d807035fa60ca757b1b27cc63c4bfce6e92070
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730770"
---
# <a name="wdsutil-get-transportserver"></a>wdsutil get transportserver

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
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil disable-transportserver コマンド](wdsutil-disable-transportserver.md)
- [wdsutil enable transportserver コマンド](wdsutil-enable-transportserver.md)
- [wdsutil set transportserver コマンド](wdsutil-set-transportserver.md)
- [wdsutil start-transportserver コマンド](wdsutil-start-transportserver.md)
- [wdsutil stop transportserver コマンド](wdsutil-stop-transportserver.md)
