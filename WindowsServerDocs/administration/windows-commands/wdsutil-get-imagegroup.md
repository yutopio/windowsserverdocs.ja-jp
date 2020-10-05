---
title: wdsutil get-imagegroup
description: Wdsutil get imagegroup の参照記事。イメージグループとその中のイメージに関する情報を取得します。
ms.topic: reference
ms.assetid: 0fc25aca-a529-44ee-bc8e-96bc8affb458
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d40fef643ebbb8fd48f36fc048ddefc0b4b3229f
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730818"
---
# <a name="wdsutil-get-imagegroup"></a>wdsutil get-imagegroup

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

イメージ グループおよびその中のイメージに関する情報を取得します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Get-ImageGroup ImageGroup:<Image group name> [/Server:<Server name>] [/detailed]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|ImageGroup<Image group name>|イメージグループの名前を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|詳細/|各イメージのイメージのメタデータを返します。 このパラメーターが使用でない場合は、既定の動作は、イメージの名前、説明、およびファイル名のみを返すには。|
## <a name="examples"></a>例
イメージ グループに関する情報を表示するには、次のように入力します。
```
wdsutil /Get-ImageGroup ImageGroup:ImageGroup1
```
メタデータを含む情報を表示するには、次のように入力します。
```
wdsutil /verbose /Get-ImageGroup ImageGroup:ImageGroup1 /Server:MyWDSServer /detailed
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil add imagegroup コマンド](wdsutil-add-imagegroup.md)
- [wdsutil get-allimagegroups コマンド](wdsutil-get-allimagegroups.md)
- [wdsutil remove-imagegroup コマンド](wdsutil-remove-imagegroup.md)
- [wdsutil set-imagegroup コマンド](wdsutil-set-imagegroup.md)
