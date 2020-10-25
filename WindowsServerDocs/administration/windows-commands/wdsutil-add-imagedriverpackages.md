---
title: wdsutil add imagedriverpackages
description: Wdsutil add imagedriverpackages コマンドのリファレンス記事。ドライバーパッケージをドライバーストアからブートイメージに追加します。
ms.topic: reference
ms.assetid: 9dc78909-a4d1-42a2-af8f-21ebcbfe8302
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 74029ca7b2243603c832b74f59a9248353cea911
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524477"
---
# <a name="wdsutil-add-imagedriverpackages"></a>wdsutil add imagedriverpackages

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ブート イメージにドライバー ストアからドライバー パッケージを追加します。

## <a name="syntax"></a>構文

```
wdsutil /add-ImageDriverPackages [/Server:<Server name>media:<Image namemediatype:Boot /Architecture:{x86 | ia64 | x64} [/Filename:<File name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value> ...]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| [メディア: `<Imagename>` ] | ドライバーを追加するイメージの名前を指定します。 |
| [mediatype: ブート] | ドライバーを追加する画像の種類を指定します。 ドライバー パッケージは、ブート イメージにのみ追加できます。 |
| [/アーキテクチャ: `{x86 | ia64 | x64}` ] | ブート イメージのアーキテクチャを指定します。 異なるアーキテクチャのブートイメージで同じイメージ名を持つことができるため、正しいイメージが使用されるようにアーキテクチャを指定する必要があります。 |
| [/ファイル名:`<Filename>`] | ファイルの名前を指定します。 イメージは、名前によって一意に識別できない、ファイル名を指定してください。 |
| Filtertype`<Filtertype>` | 検索するドライバー パッケージの属性を指定します。 1 つのコマンドでは、複数の属性を指定できます。 また、このオプションを使用して、 **/演算子** と **/値** を指定する必要があります。 有効な値は、次のとおりです。<ul><li>PackageId</li><li>PackageName</li><li>PackageEnabled</li><li>Packagedateadded</li><li>PackageInfFilename</li><li>PackageClass<p>PackageProvider</li><li>PackageArchitecture</li><li>PackageLocale</li><li>PackageSigned</li><li>PackagedatePublished 済み</li><li>Packageversion</li><li>Driverdescription</li><li>DriverManufacturer</li><li>DriverHardwareId</li><li>Driver互換 Id</li><li>DriverExcludeId</li><li>DriverGroupId</li><li>DriverGroupName * *</li></ul>. |
| Operator`{Equal|NotEqual|GreaterOrEqual|LessOrEqual|Contains}` | 属性と値間のリレーションシップを指定します。 だけを指定できます **Contains** 文字列の属性を持つ。 だけを指定できます **GreaterOrEqual** と **LessOrEqual** 日、バージョン属性を持つ。 |
| 数値`<Value>` | 指定した基準を検索する値を指定 `<attribute>`します。 1つの **/Filtertype**に対して複数の値を指定できます。 各フィルターで使用できる値は次のとおりです。<ul><li>**PackageId** -有効な GUID を指定します。 例: {4d36e972-e325-11ce-bfc1-08002be10318}</li><li>**PackageName** -任意の文字列値を指定します。</li><li>**Packageenabled** - **Yes**または**No**を指定します</li><li>**Packagedateadded** -次の形式で日付を指定します: YYYY/MM/DD</li><li>**Packageinffilename** -任意の文字列値を指定します。</li><li>**パッケージの eclass** -有効なクラス名またはクラス GUID を指定します。 例: **DiskDrive**、 **Net**、{4d36e972-e325-11ce-bfc1-08002be10318}</li><li>**Packageprovider** -任意の文字列値を指定します</li><li>**Packagearchitecture** - **x86**、 **x64**、または**ia64**を指定します。</li><li>**Packagelocale** -有効な言語識別子を指定します。 例: **en-us** または **es**</li><li>**パッケージ**: **Yes**または**No**を指定します</li><li>**Packagedatepublished** 済み-日付を YYYY/MM/DD の形式で指定します。</li><li>**Packageversion** -次の形式でバージョンを指定します: a.b.x.y. 例: 6.1.0.0</li><li>**Driverdescription** -任意の文字列値を指定します</li><li>**Drivermanufacturer** -任意の文字列値を指定します</li><li>**DriverHardwareId** -任意の文字列値を指定します。</li><li>**Driver互換 id** -任意の文字列値を指定します</li><li>**Driverexcludeid** -任意の文字列値を指定します</li><li>**Drivergroupid** -有効な GUID を指定してください。 例: {4d36e972-e325-11ce-bfc1-08002be10318}</li><li>**Drivergroupname** -任意の文字列値を指定します</li></ul> これらの値の詳細については、「 [ドライバーとパッケージの属性](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759262(v=ws.11))」を参照してください。 |

## <a name="examples"></a>例

ブート イメージにドライバー パッケージを追加するには、次のいずれかを入力します。

```
wdsutil /add-ImageDriverPackagemedia:WinPE Boot Imagemediatype:Boot /Architecture:x86 /Filtertype:DriverGroupName /Operator:Equal /Value:x86Bus /Filtertype:PackageProvider /Operator:Contains /Value:Provider1 /Filtertype:Packageversion /Operator:GreaterOrEqual /Value:6.1.0.0
```

```
wdsutil /verbose /add-ImageDriverPackagemedia: WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filtertype:PackageClass /Operator:Equal /Value:Net /Filtertype:DriverManufacturer /Operator:NotEqual /Value:Name1 /Value:Name2 /Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```

```
wdsutil /verbose /add-ImageDriverPackagemedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /Filtertype:PackageClass /Operator:Equal /Value:Net /Value:System /Value:DiskDrive /Value:HDC /Value:SCSIAdapter
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-
- [wdsutil add imagedriverpackage コマンド](wdsutil-add-imagedriverpackage.md)
-
- [wdsutil add alldriverpackages コマンド](wdsutil-add-alldriverpackages.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
