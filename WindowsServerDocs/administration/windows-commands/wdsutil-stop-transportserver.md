---
title: wdsutil 停止-transportserver
description: 停止 TransportServer のリファレンス記事
ms.topic: reference
ms.assetid: dc1b1eec-6893-445e-81dc-16b3fae287fa
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 800c99cba18ed2158749b1638627b31f8fdbaf5f
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731255"
---
# <a name="wdsutil-stop-transportserver"></a>wdsutil 停止-transportserver

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

トランスポート サーバー上のすべてのサービスを停止します。
## <a name="syntax"></a>構文
```
wdsutil [Options] /Stop-TransportServer [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|トランスポート サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 トランスポート サーバーが指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
サービスを停止するには、次のいずれかを入力します。
```
wdsutil /Stop-TransportServer
wdsutil /verbose /Stop-TransportServer /Server:MyWDSServer
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil disable-transportserver コマンド](wdsutil-disable-transportserver.md)
- [wdsutil enable transportserver コマンド](wdsutil-enable-transportserver.md)
- [wdsutil get transportserver コマンド](wdsutil-get-transportserver.md)
- [wdsutil set transportserver コマンド](wdsutil-set-transportserver.md)
- [wdsutil start-transportserver コマンド](wdsutil-start-transportserver.md)
