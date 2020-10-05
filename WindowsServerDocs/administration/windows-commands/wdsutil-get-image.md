---
title: wdsutil イメージの取得
description: イメージに関する情報を取得する wdsutil get イメージの参照記事です。
ms.topic: reference
ms.assetid: 0ecaa999-72ad-4191-adb5-a418de42a001
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0f6cfcf3783ef49f2dd57941ae9a2ae4feb3742e
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730810"
---
# <a name="wdsutil-get-image"></a>wdsutil イメージの取得

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

イメージに関する情報を取得します。

## <a name="syntax"></a>構文
ブートイメージの場合:
```
wdsutil [Options] /Get-Image image:<Image name> [/Server:<Server name> imagetype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>]
```
インストールイメージの場合:
```
wdsutil [Options] /Get-image image:<Image name> [/Server:<Server name> imagetype:Install imagegroup:<Image group name>] [/Filename:<File name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
| 絵<Image name>|イメージの名前を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
| imagetype: {Boot &#124; Install}|画像の種類を指定します。|
|/アーキテクチャ: {x86 & #124; ia64 & #124; x64}|イメージのアーキテクチャを指定します。 さまざまなアーキテクチャでブート イメージで同じイメージの名前を指定することも可能である、アーキテクチャの値を指定する適切なイメージが返されることにより、します。|
|[/ファイル名:<File name>]|名前によってイメージを一意に識別できない場合は、このオプションを使用してファイル名を指定する必要があります。|
|\ imagegroup: <Image group name> ]|イメージを含むイメージ グループを指定します。 イメージ グループが指定されていないサーバーに 1 つだけのイメージ グループが存在する場合は、そのグループが使用されます。 サーバーの 1 つ以上のイメージ グループが存在する場合は、イメージ グループを指定するこのパラメーターを使用する必要があります。|
## <a name="examples"></a>例
ブート イメージに関する情報を取得するには、次のいずれかを入力します。
```
wdsutil /Get-Image image:WinPE boot imagetype:Boot /Architecture:x86
wdsutil /verbose /Get-Image image:WinPE boot image /Server:MyWDSServer imagetype:Boot /Architecture:x86 /Filename:boot.wim
```
インストール イメージに関する情報を取得するには、次のいずれかを入力します。
```
wdsutil /Get-Image:Windows Vista with Office imagetype:Install
wdsutil /verbose /Get-Image:Windows Vista with Office /Server:MyWDSServer imagetype:Install imagegroup:ImageGroup1 /Filename:install.wim
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil のイメージの追加コマンド](wdsutil-add-image.md)
- [wdsutil コピー-イメージコマンド](wdsutil-copy-image.md)
- [wdsutil export-イメージコマンド](wdsutil-export-image.md)
- [wdsutil 削除-イメージコマンド](wdsutil-remove-image.md)
- [wdsutil replace-イメージコマンド](wdsutil-replace-image.md)
- [wdsutil set-image コマンド](wdsutil-set-image.md)
