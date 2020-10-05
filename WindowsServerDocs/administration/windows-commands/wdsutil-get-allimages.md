---
title: wdsutil get-allimages
description: サーバー上のすべてのイメージに関する情報を取得する wdsutil get のリファレンス記事。
ms.topic: reference
ms.assetid: 19de3720-4315-415a-8dc6-486caa0b2100
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: fc4234e199d0eb39c3f8d94c31f2330f60cdc167
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730882"
---
# <a name="wdsutil-get-allimages"></a>wdsutil get-allimages

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバー上のすべてのイメージに関する情報を取得します。

## <a name="syntax"></a>構文
```
wdsutil /Get-AllImages [/Server:<Server name>] /Show:{Boot | Install | LegacyRis | All} [/detailed]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|/表示: {ブートと #124 文字です。インストールと #124 文字です。LegacyRis & #124 文字です。すべて}|-   **ブート** では、ブートイメージのみが返されます。<br />-   **インストール** では、インストールイメージと、そのイメージを含むイメージグループに関する情報が返されます。<br />-   **LegacyRis** は、リモートインストールサービス (RIS) のイメージのみを返します。<br />-   **すべて** のブートイメージ情報、インストールイメージ情報 (イメージグループに関する情報を含む)、および RIS イメージ情報が返されます。|
|詳細/|各イメージからすべてのイメージのメタデータを返すことを示します。 このオプションを使用しない場合、既定の動作は、イメージの名前、説明、およびファイル名のみを返すには。|
## <a name="examples"></a>例
イメージに関する情報を表示するには、次のいずれかを入力します。
```
wdsutil /Get-AllImages /Show:Install
wdsutil /verbose /Get-AllImages /Server:MyWDSServer /Show:All /detailed
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil のイメージの追加コマンド](wdsutil-add-image.md)
- [wdsutil コピー-イメージコマンド](wdsutil-copy-image.md)
- [wdsutil export-イメージコマンド](wdsutil-export-image.md)
- [wdsutil 削除-イメージコマンド](wdsutil-remove-image.md)
- [wdsutil replace-イメージコマンド](wdsutil-replace-image.md)
- [wdsutil set-image コマンド](wdsutil-set-image.md)
