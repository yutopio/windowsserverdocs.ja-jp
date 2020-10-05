---
title: wdsutil get サーバー
description: 指定された Windows 展開サービスサーバーから情報を取得する wdsutil get server のリファレンス記事です。
ms.topic: reference
ms.assetid: bef60db4-d58d-4304-ab4b-be53dd3271c3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e855724833a90c64dfb3692ccd82fad67a572873
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730778"
---
# <a name="wdsutil-get-server"></a>wdsutil get サーバー

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定した Windows 展開サービス サーバーから情報を取得します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Get-Server [/Server:<Server name>] /Show:{Config | Images | All} [/detailed]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。|
|/表示: {Config & #124 文字です。イメージと #124 文字です。すべて}|返される情報の種類を指定します。<p>-   **Config** は構成情報を返します。<br />-   **イメージは** 、イメージグループ、ブートイメージ、およびインストールイメージに関する情報を返します。<br />-   **All** は、構成情報とイメージ情報を返します。|
|詳細/|このオプションを使用することができます **/Show:Images** または **/Show:All** を指定する各イメージからすべてのイメージのメタデータを返す必要があります。 **/Detailed**オプションが使用されていない場合、既定の動作では、イメージの名前、説明、およびファイル名が返されます。|
## <a name="examples"></a>例
サーバーに関する情報を表示するには、次のように入力します。
```
wdsutil /Get-Server /Show:Config
```
サーバーに関する詳細情報を表示するには、次のように入力します。
```
wdsutil /verbose /Get-Server /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil disable-サーバーコマンド](wdsutil-disable-server.md)
- [wdsutil enable-サーバーコマンド](wdsutil-enable-server.md)
- [wdsutil initialize-サーバーコマンド](wdsutil-initialize-server.md)
- [wdsutil set-サーバーコマンド](wdsutil-set-server.md)
- [wdsutil start-サーバーコマンド](wdsutil-start-server.md)
- [wdsutil stop-サーバーコマンド](wdsutil-stop-server.md)
- [wdsutil 初期化解除-サーバーコマンド](wdsutil-uninitialize-server.md)
