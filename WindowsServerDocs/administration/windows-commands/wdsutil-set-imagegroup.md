---
title: wdsutil set-imagegroup
description: イメージグループの属性を変更するサブコマンドの set ImageGroup のリファレンス記事です。
ms.topic: reference
ms.assetid: 4d86946a-e261-4d41-8b0c-1ab0ba2e3430
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6f3b2b3790ecc126f8be48ade61d305d44011f68
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731325"
---
# <a name="wdsutil-set-imagegroup"></a>wdsutil set-imagegroup

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

イメージグループの属性を変更します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /set-imagegroup:<Image group name> [/Server:<Server name>] [/Name:<New image group name>] [/Security:<SDDL>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|/set-imagegroup:<Image group name>|イメージグループの名前を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 指定しない場合、ローカル サーバーが使用されます。|
|[/Name:<New image group name>]|イメージグループの新しい名前を指定します。|
|[セキュリティ: <SDDL> ]|セキュリティ記述子定義言語 (SDDL) 形式で、イメージグループの新しいセキュリティ記述子を指定します。|
## <a name="examples"></a>例
イメージグループの名前を設定するには、次のように入力します。
```
wdsutil /Set-ImageGroup:ImageGroup1 /Name:New Image Group Name
```
イメージグループのさまざまな設定を指定するには、次のように入力します。
```
wdsutil /verbose /Set-ImageGroupGroup:ImageGroup1 /Server:MyWDSServer /Name:New Image Group Name
/Security:O:BAG:S-1-5-21-2176941838-3499754553-4071289181-513 D:AI(A;ID;FA;;;SY)(A;OICIIOID;GA;;;SY)(A;ID;FA;;;BA)(A;OICIIOID;GA;;;BA) (A;ID;0x1200a9;;;AU)(A;OICIIOID;GXGR;;;AU)
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil add imagegroup コマンド](wdsutil-add-imagegroup.md)
- [wdsutil get-allimagegroups コマンド](wdsutil-get-allimagegroups.md)
- [wdsutil get imagegroup コマンド](wdsutil-get-imagegroup.md)
- [wdsutil remove-imagegroup コマンド](wdsutil-remove-imagegroup.md)
