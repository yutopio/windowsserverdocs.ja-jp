---
title: wdsutil 追加-imagegroup
description: Windows 展開サービスサーバーにイメージグループを追加する wdsutil add imagegroup のリファレンス記事です。
ms.topic: reference
ms.assetid: 6ca88671-51de-4924-b969-88f3dfd84270
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 97f1439a4212a770dff6f6c42837c531f08c3d25
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731050"
---
# <a name="wdsutil-add-imagegroup"></a>wdsutil 追加-imagegroup

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービス サーバーには、イメージ グループを追加します。

## <a name="syntax"></a>構文
```
wdsutil [Options] /add-ImageGroup imageGroup:<Image group name> [/Server:<Server name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|imagegroup<Image group name>|追加するイメージ グループの名前を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
## <a name="examples"></a>例
イメージ グループを追加するには、次のいずれかを入力します。
```
wdsutil /add-ImageGroup imageGroup:ImageGroup2
wdsutil /verbose /add-Imagegroup imageGroup:My Image Group /Server:MyWDSServer
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil get-allimagegroups コマンド](wdsutil-get-allimagegroups.md)
- [wdsutil get imagegroup コマンド](wdsutil-get-imagegroup.md)
- [wdsutil remove-imagegroup コマンド](wdsutil-remove-imagegroup.md)
- [wdsutil set-imagegroup コマンド](wdsutil-set-imagegroup.md)
