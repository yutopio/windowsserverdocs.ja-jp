---
title: wdsutil/get-multicasttransmission
description: Wdsutil/get-multicasttransmission のリファレンス記事。イメージの新しいマルチキャスト転送を作成します。
ms.topic: reference
ms.assetid: c1f1dc46-dd50-4eb9-9f72-cf0e5d71bd3d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4b02668a6e714ce090a013a34d9dee73121f7a89
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730713"
---
# <a name="wdsutil-new-multicasttransmission"></a>wdsutil/get-multicasttransmission

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

イメージのマルチキャスト転送を新しいを作成します。 このコマンドは、Windows 展開サービス mmc スナップインを使用して転送を作成することと同じです ([ **マルチキャスト転送** ] ノードを右クリックし、[ **マルチキャスト転送**] をクリックします)。 展開サーバーの役割サービスと、トランスポート サーバー役割サービスがインストールされる既定のインストール) の両方がある場合は、このコマンドを使用する必要があります。 トランスポートサーバーの役割サービスのみがインストールされている場合は、 [wdsutilnew コマンド](wdsutil-new-namespace.md)を使用します。
## <a name="syntax"></a>構文
インストールイメージの転送:
```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      imagetype:Install
       ImageGroup:<Image Group>]
        [/Filename:<File name>]
```
ブートイメージの転送の場合 (Windows Server 2008 R2 でのみサポートされます):
```
wdsutil [Options] /New-MulticastTransmissiomedia:<Image name>
        [/Server:<Server name>]
        /FriendlyName:<Friendly name>
        [/Description:<Description>]
        /Transmissiontype: {AutoCast | ScheduledCast}
            [/time:<YYYY/MM/DD:hh:mm>]
            [/Clients:<Num of Clients>]
      imagetype:Boot
        /Architecture:{x86 | ia64 | x64}
        [/Filename:<File name>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
| dism.exe<Image name>|マルチキャストを使用して転送するイメージの名前を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|フレンドリ<Friendly name>|転送のフレンドリ名を指定します。|
|/Description<Description>]|送信の説明を指定します。|
| /imagetype: {Boot&#124;Install}|マルチキャストを使用して転送する画像の種類を指定します。 注 **ブート** は Windows Server 2008 R2 でのみサポートされます。|
| /ImageGroup: <Image group name> ]|イメージを含むイメージ グループを指定します。 イメージ グループ名が指定されていないサーバーに 1 つだけのイメージ グループが存在する場合は、そのイメージ グループを使用します。 サーバーの 1 つ以上のイメージ グループが存在する場合は、イメージ グループ名を指定するこのオプションを使用する必要があります。|
|[/ファイル名:<File name>]|ファイル名を指定します。 場合は、ソース イメージは、名前によって一意に識別できない、ファイル名を指定するこのオプションを使用する必要があります。|
|/Transmissiontype: {AutoCast &#124; ScheduledCast}|転送を自動的に開始するかどうかを指定します (オート) か、指定した開始条件 (キャスト) を基にします。<p><ul><li>**自動キャスト**します。 この転送の型は、該当するクライアントは、インストール イメージを要求するように選択したイメージのマルチキャスト転送が開始することを示します。 既に開始されている転送に参加する他のクライアントが同じイメージを要求するとします。</li><li>**スケジュールされたキャスト**します。 この転送型では、イメージや、特定の曜日と時刻を要求するクライアントの数に基づいて、転送の開始条件を設定します。 次のオプションを選択できます。<p><ul><li>[/時刻: <time> ]-YYYY/MM/DD: hh: mm の形式を使用して、転送を開始する時刻を設定します。</li><li>[/クライアント: <Number of clients>]-クライアントから送信が開始する前に待機するの最小数を設定します。</li></ul></li></ul>|
|/アーキテクチャ: {x86 & #124; ia64 & #124; x64}|マルチキャストを使用して送信するブート イメージのアーキテクチャを指定します。 さまざまなアーキテクチャのブート イメージで同じ名前を持つことなので、確実に適切なイメージが使用されるアーキテクチャを指定してください。|
|[/ファイル名:<File name>]|ファイル名を指定します。 ソース イメージは、名前によって一意に識別できない場合、は、ファイル名を指定する必要があります。|
## <a name="examples"></a>例
Windows Server 2008 R2 では、ブート イメージの自動キャスト転送を作成するに次のように入力します。
```
wdsutil /New-MulticastTransmission /FriendlyName:WDS Boot Transmission
/Image:X64 Boot imagetype:Boot /Architecture:x64 /Transmissiontype:AutoCast
```
自動キャスト転送は、インストール イメージを作成するには、次のように入力します。
```
wdsutil /New-MulticastTransmission /FriendlyName:WDS AutoCast Transmission
/Image:Vista with Officeimage imagetype:Install /Transmissiontype:AutoCast
```
インストール イメージのスケジュールされたキャスト転送を作成するには、次のように入力します。
```
wdsutil /New-MulticastTransmission /FriendlyName:WDS SchedCast Transmission /Server:MyWDSServer Image:Vista with Office imagetype:Install
/Transmissiontype:ScheduledCast /time:2006/11/20:17:00 /Clients:100
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil allmulticasttransmissions コマンド](wdsutil-get-allmulticasttransmissions.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-get-multicasttransmission.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-remove-multicasttransmission.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-start-multicasttransmission.md)
