---
title: wdsutil の追加-イメージ
description: Windows 展開サービスサーバーにイメージを追加する wdsutil add-image のリファレンス記事です。
ms.topic: reference
ms.assetid: d5b6f4da-90ba-4b0e-9423-66c8ef5172e2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ef8068f45a8a2d49715420c06859d326bf93200a
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731086"
---
# <a name="wdsutil-add-image"></a>wdsutil の追加-イメージ

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービス サーバーにイメージを追加します。

## <a name="syntax"></a>構文
ブートイメージの場合は、次の構文を使用します。
```
wdsutil /add-Image imageFile:<wim file path> [/Server:<Server name> imagetype:Boot [/Skipverify] [/Name:<Image name>] [/Description:<Image description>]
[/Filename:<New wim file name>]
```
インストールイメージの場合は、次の構文を使用します。
```
wdsutil /add-Image imageFile:<wim file path>
     [/Server:<Server name>]
    imagetype:Install
     [/Skipverify]
     imageGroup:<Image group name>]
     [/SingleImage:<Single image name>]
         [/Name:<Name>]
         [/Description:<Description>]
     [/Filename:<File name>]
     [/UnattendFile:<Unattend file path>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|イメージファイル: < .wim ファイルパス>|追加するイメージを含む Windows イメージ (.wim) ファイルの完全パスとファイル名を指定します。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
| imagetype: {Boot&#124;Install}|追加するイメージの種類を指定します。|
|[/Skipverify]|ある整合性の検証は実行されません、ソース イメージ ファイルのイメージを追加する前に指定します。|
|[/Name:<Name>]|イメージの表示名を設定します。|
|/Description<Description>]|イメージの説明を設定します。|
|[/ファイル名:<Filename>]|.Wim ファイルの新しいファイル名を指定します。 これにより、イメージを追加するときに、.wim ファイルのファイル名を変更することができます。 ファイル名が指定されていない場合、ソース イメージ ファイル名が使用されます。 常に、Windows 展開サービスをセットアップ先のコンピューターのブート イメージ ストアにファイル名が一意かどうかをチェックします。|
|\ imagegroup: <Image group name> ]|イメージが追加されるイメージ グループの名前を指定します。 サーバーの 1 つ以上のイメージ グループが存在する場合は、イメージ グループを指定してください。 これが指定されていないイメージ グループが存在しない場合は、新しいイメージ グループが作成されます。 それ以外の場合、既存のイメージ グループが使用されます。|
|[/Singleimage: <Single image name> ][/Name: <Name> ]/Description<Description>]|.Wim ファイルから指定された 1 つのイメージをコピーし、イメージの表示名と説明を設定します。|
|[/UnattendFile:<Unattend file path>]|無人インストール ファイルが追加されているイメージと関連付けるへの完全パスを指定します。 場合 **/SingleImage** が指定されていない、同じ無人セットアップ ファイルはすべての .wim ファイル内のイメージに関連付けられます。|
## <a name="examples"></a>例
ブート イメージを追加するには、次のように入力します。
```
wdsutil /add-Image imageFile:C:\MyFolder\Boot.wim imagetype:Boot
wdsutil /verbose /Progress /add-Image imageFile:\\MyServer\Share\Boot.wim /Server:MyWDSServer imagetype:Boot /Name:My WinPE Image
/Description:WinPE Image containing the WDS Client /Filename:WDSBoot.wim
```
インストール イメージを追加するには、次のいずれかを入力します。
```
wdsutil /add-Image imageFile:C:\MyFolder\Install.wim imagetype:Install
wdsutil /verbose /Progress /add-Image imageFile:\\MyServer\Share \Install.wim /Server:MyWDSServer imagetype:Instal imageGroup:ImageGroup1
/SingleImage:Windows Pro /Name:My WDS Image
/Description:Windows Pro image with Microsoft Office /Filename:Win Pro.wim /UnattendFile:\\server\share\unattend.xml
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil コピー-イメージコマンド](wdsutil-copy-image.md)
- [wdsutil export-イメージコマンド](wdsutil-export-image.md)
- [wdsutil get イメージコマンド](wdsutil-get-image.md)
- [wdsutil 削除-イメージコマンド](wdsutil-remove-image.md)
- [wdsutil replace-イメージコマンド](wdsutil-replace-image.md)
- [wdsutil set-image コマンド](wdsutil-set-image.md)
