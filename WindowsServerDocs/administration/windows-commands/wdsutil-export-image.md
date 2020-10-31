---
title: wdsutil export-イメージ
description: Wdsutil export-image コマンドのリファレンス記事。既存のイメージをイメージストアから別の Windows イメージ (.wim) ファイルにエクスポートします。
ms.topic: reference
ms.assetid: a9b8b467-0f2d-4754-8998-55503a262778
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8c3c390e43cc8707d8d94ade757130276b5f2753
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93071044"
---
# <a name="wdsutil-export-image"></a>wdsutil export-イメージ

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

既存のイメージをイメージ ストアから別の Windows イメージ (.wim) ファイルにエクスポートします。

## <a name="syntax"></a>Syntax

ブートイメージの場合:

```
wdsutil [options] /Export-Image image:<Image name> [/Server:<Servername>]
    imagetype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<Filename>]
     /DestinationImage
         /Filepath:<Filepath and name>
         [/Name:<Name>]
         [/Description:<Description>]
     [/Overwrite:{Yes | No}]
```

インストール イメージの場合。

```
wdsutil [options] /Export-Image image:<Image name> [/Server:<Servername>]
    imagetype:Install imageGroup:<Image group name>]
     [/Filename:<Filename>]
     /DestinationImage
         /Filepath:<Filepath and name>
         [/Name:<Name>]
         [/Description:<Description>]
     [/Overwrite:{Yes | No | append}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| 絵`<Imagename>` | エクスポートするイメージの名前を指定します。 |
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。 |
| imagetype`{Boot|Install}` | エクスポートする画像の種類を指定します。 |
| \ imagegroup: `<Image group name>` ] | エクスポートするイメージを含むイメージ グループを指定します。 イメージ グループ名が指定されていないサーバーに 1 つだけのイメージ グループが存在する場合は、そのイメージ グループが既定で使用されます。 サーバーの 1 つ以上のイメージ グループが存在する場合は、イメージ グループを指定してください。 |
| 構造`{x86|ia64|x64}` | エクスポートするイメージのアーキテクチャを指定します。 さまざまなアーキテクチャでブート イメージで同じイメージの名前を持つことなのではアーキテクチャの値を指定する適切なイメージが必ず返されるようにします。 |
| [/ファイル名:`<Filename>`] | イメージを名前で一意に識別できない場合は、ファイル名を指定する必要があります。 |
| /DestinationImage | コピー先の画像の設定を指定します。 次のオプションを使用してこれらの設定を指定することができます。<ul><li>`/Filepath:<Filepath and name>` -新しいイメージの完全なファイルパスを指定します。</li><li>`[/Name:<Name>]` -イメージの表示名を設定します。 名が指定されていない場合は、ソース イメージの表示名が使用されます。</li><li>`[/Description: <Description>]` -イメージの説明を設定します。</li></ul> |
| [/Overwrite: `{Yes|No|append}` ] | /Filepath にその名前の既存のファイルが既に存在する場合に、 **/destinationimage** オプションで指定されたファイルを上書きするかどうかを指定します。 **[はい** ] オプションを指定すると、既存のファイルが上書きされます。 [ **いいえ** ] オプション (既定) の場合、同じ名前のファイルが既に存在するとエラーが発生し、[ **追加** ] オプションを指定すると、生成されたイメージが既存の .wim ファイル内に新しいイメージとして追加されます。 |

## <a name="examples"></a>例

ブートイメージをエクスポートするには、次のいずれかを入力します。

```
wdsutil /Export-Image image:WinPE boot image imagetype:Boot /Architecture:x86 /DestinationImage /Filepath:C:\temp\boot.wim
```

```
wdsutil /verbose /Progress /Export-Image image:WinPE boot image /Server:MyWDSServer imagetype:Boot /Architecture:x64 /Filename:boot.wim /DestinationImage /Filepath:\\Server\Share\ExportImage.wim /Name:Exported WinPE image /Description:WinPE Image from WDS server /Overwrite:Yes
```

インストールイメージをエクスポートするには、次のいずれかを入力します。

```
wdsutil /Export-Image image:Windows Vista with Office imagetype:Install /DestinationImage /Filepath:C:\Temp\Install.wim
```

```
wdsutil /verbose /Progress /Export-Image image:Windows Vista with Office /Server:MyWDSServer imagetype:Instal imageGroup:ImageGroup1 /Filename:install.wim /DestinationImage /Filepath:\\server\share\export.wim /Name:Exported Windows image /Description:Windows Vista image from WDS server /Overwrite:append
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil のイメージの追加コマンド](wdsutil-add-image.md)

- [wdsutil コピー-イメージコマンド](wdsutil-copy-image.md)

- [wdsutil get イメージコマンド](wdsutil-get-image.md)

- [wdsutil 削除-イメージコマンド](wdsutil-remove-image.md)

- [wdsutil replace-イメージコマンド](wdsutil-replace-image.md)

- [wdsutil set-image コマンド](wdsutil-set-image.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)