---
title: wdsutil の追加-イメージ
description: Windows 展開サービスサーバーにイメージを追加する wdsutil add image コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: d5b6f4da-90ba-4b0e-9423-66c8ef5172e2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e0d80c0a3aa9cfc6a5b9e05f11542dfcc8621946
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524519"
---
# <a name="wdsutil-add-image"></a>wdsutil の追加-イメージ

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービス サーバーにイメージを追加します。

## <a name="syntax"></a>構文

ブート イメージには、次の構文を使用します。

```
wdsutil /add-Image imageFile:<wim file path> [/Server:<Server name> imagetype:Boot [/Skipverify] [/Name:<Image name>] [/Description:<Image description>] [/Filename:<New wim file name>]
```

インストール イメージには、次の構文を使用します。

```
wdsutil /add-Image imageFile:<wim filepath> [/Server:<Servername>] imagetype:Install [/Skipverify] imageGroup:<Image group name>] [/SingleImage:<Single image name>] [/Name:<Name>] [/Description:<Description>] [/Filename:<File name>] [/UnattendFile:<Unattend file path>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| イメージ`<.wim filepath>` | 追加するイメージを含む Windows イメージ (.wim) ファイルの完全パスとファイル名を指定します。 |
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| imagetype`{Boot|Install}` | 追加するイメージの種類を指定します。 |
| [/Skipverify] | ある整合性の検証は実行されません、ソース イメージ ファイルのイメージを追加する前に指定します。 |
| [/Name:`<Name>`] | イメージの表示名を設定します。 |
| [/説明:`<Description>`] | イメージの説明を設定します。 |
| [/ファイル名:`<Filename>`] | .Wim ファイルの新しいファイル名を指定します。 これにより、イメージを追加するときに、.wim ファイルのファイル名を変更することができます。 ファイル名を指定しない場合は、ソースイメージファイル名が使用されます。 常に、Windows 展開サービスをセットアップ先のコンピューターのブート イメージ ストアにファイル名が一意かどうかをチェックします。 |
| \ imagegroup: `<Imagegroupname>` ] | イメージが追加されるイメージ グループの名前を指定します。 サーバーの 1 つ以上のイメージ グループが存在する場合は、イメージ グループを指定してください。 イメージグループを指定せず、イメージグループがまだ存在しない場合は、新しいイメージグループが作成されます。 それ以外の場合は、既存のイメージグループが使用されます。 |
| [/[Singleimage]:`<Singleimagename>`][/Name:`<Name>`][/説明:`<Description>`] | .Wim ファイルから指定された 1 つのイメージをコピーし、イメージの表示名と説明を設定します。 |
| [/UnattendFile:`<Unattendfilepath>`] | 無人インストール ファイルが追加されているイメージと関連付けるへの完全パスを指定します。 **/Singleimage**が指定されていない場合、同じ無人セットアップファイルが、.wim ファイル内のすべてのイメージに関連付けられます。 |

## <a name="examples"></a>例

ブート イメージを追加するには、次のように入力します。

```
wdsutil /add-Image imageFile:C:\MyFolder\Boot.wim imagetype:Boot
wdsutil /verbose /Progress /add-Image imageFile:\\MyServer\Share\Boot.wim /Server:MyWDSServer imagetype:Boot /Name:My WinPE Image /Description:WinPE Image containing the WDS Client /Filename:WDSBoot.wim
```

インストール イメージを追加するには、次のいずれかを入力します。

```
wdsutil /add-Image imageFile:C:\MyFolder\Install.wim imagetype:Install
wdsutil /verbose /Progress /add-Image imageFile:\\MyServer\Share \Install.wim /Server:MyWDSServer imagetype:Instal imageGroup:ImageGroup1
/SingleImage:Windows Pro /Name:My WDS Image /Description:Windows Pro image with Microsoft Office /Filename:Win Pro.wim /UnattendFile:\\server\share\unattend.xml
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil コピー-イメージコマンド](wdsutil-copy-image.md)

- [wdsutil export-イメージコマンド](wdsutil-export-image.md)

- [wdsutil get イメージコマンド](wdsutil-get-image.md)

- [wdsutil 削除-イメージコマンド](wdsutil-remove-image.md)

- [wdsutil replace-イメージコマンド](wdsutil-replace-image.md)

- [wdsutil set-image コマンド](wdsutil-set-image.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
