---
title: wdsutil add imagedriverpackage
description: Wdsutil add imagedriverpackage のリファレンス記事。ドライバーストア内のドライバーパッケージをサーバー上の既存のブートイメージに追加します。
ms.topic: reference
ms.assetid: 6c2a4833-6427-47f8-9ffb-20b3786cb406
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5a85e64f39b360b5e970a15bd0da85326d67b06a
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731075"
---
# <a name="wdsutil-add-imagedriverpackage"></a>wdsutil add imagedriverpackage

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバー上の既存のブート イメージにドライバー ストアに含まれるドライバー パッケージを追加します。 イメージのバージョンは、Windows 7 または Windows Server 2008 R2 をする必要がありますまたはそれ以降。

## <a name="syntax"></a>構文
```
wdsutil /add-ImageDriverPackage [/Server:<Server name>media:<Image namemediatype:Boot /Architecture:{x86 | ia64 | x64}
```
```
[/Filename:<File name>] {/DriverPackage:<Package Name> | /PackageId:<ID>}
```
### <a name="parameters"></a>パラメーター

|                 パラメーター                  |                                                                                                                                                                                                            説明                                                                                                                                                                                                             |
|--------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|           /Server<Server name>           |                                                                                                                                               サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。                                                                                                                                                |
|             用紙<Image name>             |                                                                                                                                                                                       ドライバーを追加するイメージの名前を指定します。                                                                                                                                                                                        |
|               mediatype: ブート               |                                                                                                                                                                ドライバーを追加する画像の種類を指定します。 ドライバー パッケージは、ブート イメージにのみ追加できます。                                                                                                                                                                 |
| /アーキテクチャ: {x86 & #124; ia64 & #124; x64} |                                                                                                       ブート イメージのアーキテクチャを指定します。 さまざまなアーキテクチャでブート イメージで同じイメージの名前を指定することも可能であるために、確実に適切なイメージが使用されるアーキテクチャを指定してください。                                                                                                        |
|           /ファイル名:<File name>]           |                                                                                                                                                        ファイルの名前を指定します。 イメージは、名前によって一意に識別できない、ファイル名を指定してください。                                                                                                                                                        |
|           [/Driverpackage:<Name>           |                                                                                                                                                                                   イメージに追加するドライバー パッケージの名前を指定します。                                                                                                                                                                                    |
|             [/パッケージ Id:<ID>]              | ドライバーパッケージの Windows 展開サービス ID を指定します。 ドライバー パッケージを名前によって一意に識別できない場合は、このオプションを指定する必要があります。 パッケージ ID を検索するには、パッケージがドライバー グループをクリックして (または **すべてのパッケージ** ノード)、パッケージを右クリックし、[クリックして **プロパティ**します。 [ **全般** ] タブにパッケージ ID が表示されます。例: {DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}。 |

## <a name="examples"></a>例
ブート イメージにドライバー パッケージを追加するには、次のいずれかを入力します。
```
wdsutil /add-ImageDriverPackagmedia:WinPE Boot Imagemediatype:Boot /Architecture:x86 /DriverPackage:XYZ
```
```
wdsutil /verbose /add-ImageDriverPackagmedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil add imagedriverpackages コマンド](wdsutil-add-imagedriverpackages.md)
