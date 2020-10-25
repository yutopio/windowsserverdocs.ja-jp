---
title: wdsutil コピー-イメージ
description: 同じイメージグループ内のイメージをコピーする、wdsutil コピーイメージコマンドの参照記事。
ms.topic: reference
ms.assetid: bea41cf4-36e6-4181-afa5-00170ebd4fdc
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 690040a5f6624e33e01969a77806afb01c815ea9
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524907"
---
# <a name="wdsutil-copy-image"></a>wdsutil コピー-イメージ

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

同じイメージ グループ内にあるイメージをコピーします。 イメージグループ間でイメージをコピーするには、 [wdsutil Export-Image コマンド](wdsutil-export-image.md) コマンドを使用し、次に [wdsutil add image コマンド](wdsutil-add-image.md) を使用します。

## <a name="syntax"></a>構文

```
wdsutil [Options] /copy-Image image:<Image name> [/Server:<Server name>] imagetype:Install imageGroup:<Image group name>] [/Filename:<File name>] /DestinationImage /Name:<Name> /Filename:<File name> [/Description:<Description>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| 絵`<Imagename>` | コピーするイメージの名前を指定します。 |
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| imagetype: Install | コピーするイメージの種類を指定します。 このオプションを設定する必要があります **インストール**します。 |
| \ imagegroup: `<Image groupname>` ] | コピーするイメージを含むイメージ グループを指定します。 イメージグループが指定されておらず、サーバー上にグループが1つしか存在しない場合は、そのイメージグループが既定で使用されます。 サーバーの 1 つ以上のイメージ グループが存在する場合は、イメージ グループを指定する必要があります。 |
| [/ファイル名:`<Filename>`] | コピーするイメージのファイル名を指定します。 ソース イメージは、名前によって一意に識別できない場合、は、ファイル名を指定する必要があります。 |
| /DestinationImage | コピー先の画像の設定を指定します。 有効な値は次のとおりです。<ul><li>/Name: `<Name>` -コピーするイメージの表示名を設定します。</li><li>/ファイル名: `<Filename>` -イメージのコピーを格納するイメージファイルの名前を設定します。</li><li>[/Description: `<Description>` ]-イメージコピーの説明を設定します。</li></ul> |

## <a name="examples"></a>例

指定されたイメージのコピーを作成し、WindowsVista.wim という名前を付けて、次のように入力します。

```
wdsutil /copy-Image image:Windows Vista with Office imagetype:Install /DestinationImage /Name:copy of Windows Vista with Office / Filename:WindowsVista.wim
```

指定されたイメージのコピーを作成するには、指定した設定を適用し、名前を WindowsVista.wim、型のコピー。

```
wdsutil /verbose /Progress /copy-Image image:Windows Vista with Office /Server:MyWDSServe imagetype:Install imageGroup:ImageGroup1
/Filename:install.wim /DestinationImage /Name:copy of Windows Vista with Office /Filename:WindowsVista.wim /Description:This is a copy of the original Windows image with Office installed
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil のイメージの追加コマンド](wdsutil-add-image.md)

- [wdsutil export-イメージコマンド](wdsutil-export-image.md)

- [wdsutil get イメージコマンド](wdsutil-get-image.md)

- [wdsutil 削除-イメージコマンド](wdsutil-remove-image.md)

- [wdsutil replace-イメージコマンド](wdsutil-replace-image.md)

- [wdsutil set-image コマンド](wdsutil-set-image.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
