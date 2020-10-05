---
title: wdsutil/get-multicasttransmission
description: 指定されたイメージのマルチキャスト転送に関する情報を表示する、wdsutil/get-multicasttransmission の参照記事。
ms.topic: reference
ms.assetid: b733737b-1e81-43d4-a058-d6985a613bef
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ceb31ea1d1d9a266c7b8ab13a859275140b98317
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730786"
---
# <a name="wdsutil-get-multicasttransmission"></a>wdsutil/get-multicasttransmission

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定したイメージのマルチキャスト転送に関する情報を表示します。

## <a name="syntax"></a>構文
**Windows Server 2008**
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name> [/Server:<Server name>mediatype:InstallmediaGroup:<Image group name>]
[/Filename:<File name>] [/Show:Clients]
```
**Windows Server 2008 R2** ブートイメージの転送:
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
    [/Server:<Server name>]
    [/details:Clients]
  mediatype:Boot
    /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
インストールイメージの転送:
```
wdsutil [Options] /Get-MulticastTransmissiomedia:<Image name>
         [/Server:<Server name>]
         [/details:Clients]
       mediatype:Install
    mediaGroup:<Image Group>]
     [/Filename:<File name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
用紙<Image name>|このイメージに関連付けられているマルチキャスト転送を表示します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。|
|/imagetype: インストール|イメージの種類を指定します。 このオプションに設定する必要があります **インストール**します。|
|/imagegroup: <Image group name> ]|イメージを含むイメージ グループを指定します。 イメージ グループ名が指定されていないサーバーに 1 つだけのイメージ グループが存在する場合は、そのイメージ グループを使用します。 サーバーの 1 つ以上のイメージ グループが存在する場合は、イメージ グループを指定するこのオプションを使用する必要があります。|
|/アーキテクチャ: {x86 & #124; ia64 & #124; x64}|転送に関連付けられているブート イメージのアーキテクチャを指定します。 さまざまなアーキテクチャでブート イメージで同じイメージの名前を指定することも可能であるために、適切なイメージが使用されるようにするアーキテクチャを指定してください。|
|[/ファイル名:<File name>]|イメージを含むファイルを指定します。 イメージは、名前によって一意に識別できない場合、は、ファイル名を指定するこのオプションを使用する必要があります。|
|[/ショー: クライアント]<p>or<p>[詳細: クライアント]|マルチキャスト転送に接続されているクライアント コンピューターに関する情報を表示します。|
## <a name="examples"></a>例
**Windows Server 2008** "Vista with Office" という名前のイメージの転送に関する情報を表示するには、次のいずれかを入力します。
```
wdsutil /Get-MulticastTransmission:Vista with Office imagetype:Install
wdsutil /Get-MulticastTransmission /Server:MyWDSServer image:Vista with Office imagetype:Install imageGroup:ImageGroup1 /Filename:install.wim /Show:Clients
```
**Windows Server 2008 R2** "Vista with Office" という名前のイメージの転送に関する情報を表示するには、次のいずれかを入力します。
```
wdsutil /Get-MulticastTransmission:Vista with Office
 /Imagetype:Install
```
```
wdsutil /Get-MulticastTransmission /Server:MyWDSServer image:Vista with Office imagetype:Install ImageGroup:ImageGroup1 /Filename:install.wim /details:Clients
```
```
wdsutil /Get-MulticastTransmission /Server:MyWDSServer:X64 Boot Imagetype:Boot /Architecture:x64 /Filename:boot.wim /details:Clients
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil allmulticasttransmissions コマンド](wdsutil-get-allmulticasttransmissions.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-new-multicasttransmission.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-remove-multicasttransmission.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-start-multicasttransmission.md)
