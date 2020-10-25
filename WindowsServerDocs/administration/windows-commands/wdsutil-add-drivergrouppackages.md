---
title: wdsutil add drivergrouppackages
description: ドライバーグループパッケージを追加する wdsutil add drivergrouppackages コマンドの参照記事です。
ms.topic: reference
ms.assetid: 29022f53-ce14-4b2d-a81a-679c18e022b2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 67e211207f2c715053d734d659d511c61337e393
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524537"
---
# <a name="wdsutil-add-drivergrouppackages"></a>wdsutil add drivergrouppackages

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ドライバーグループパッケージを追加します。

## <a name="syntax"></a>構文

```
wdsutil /add-DriverGroupPackages /DriverGroup:<Group Name> [/Server:<Server Name>] /Filtertype:<Filter type> /Operator:{Equal | NotEqual | GreaterOrEqual | LessOrEqual | Contains} /Value:<Value> [/Value:<Value>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| DriverGroup`<Groupname>` | 新しいドライバー グループの名前を指定します。 |
| Server`<Servername>` | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| Filtertype`<Filtertype>` | 検索するドライバーパッケージの種類を指定します。 1 つのコマンドでは、複数の属性を指定できます。 また、このオプションを使用して、 **/演算子** と **/値** を指定する必要があります。 有効な値は、次のとおりです。<ul><li>PackageId</li><li>PackageName</li><li>PackageEnabled</li><li>Packagedateadded</li><li>PackageInfFilename</li><li>PackageClass<p>PackageProvider</li><li>PackageArchitecture</li><li>PackageLocale</li><li>PackageSigned</li><li>PackagedatePublished 済み</li><li>Packageversion</li><li>Driverdescription</li><li>DriverManufacturer</li><li>DriverHardwareId</li><li>Driver互換 Id</li><li>DriverExcludeId</li><li>DriverGroupId</li><li>DriverGroupName * *</li></ul>. |
| Operator`{Equal|NotEqual|GreaterOrEqual|LessOrEqual|Contains}` | 属性と値間のリレーションシップを指定します。 だけを指定できます **Contains** 文字列の属性を持つ。 だけを指定できます **等しい**, 、**NotEqual**, 、**GreaterOrEqual** と **LessOrEqual** 日、バージョン属性を持つ。 |
| 数値`<Value>` | **/Filtertype**に対応するクライアント値を指定します。 1つの **/Filtertype**に対して複数の値を指定できます。 各フィルターで使用できる値は次のとおりです。<ul><li>**PackageId** -有効な GUID を指定します。 例: {4d36e972-e325-11ce-bfc1-08002be10318}</li><li>**PackageName** -任意の文字列値を指定します。</li><li>**Packageenabled** - **Yes**または**No**を指定します</li><li>**Packagedateadded** -次の形式で日付を指定します: YYYY/MM/DD</li><li>**Packageinffilename** -任意の文字列値を指定します。</li><li>**パッケージの eclass** -有効なクラス名またはクラス GUID を指定します。 例: **DiskDrive**、 **Net**、{4d36e972-e325-11ce-bfc1-08002be10318}</li><li>**Packageprovider** -任意の文字列値を指定します</li><li>**Packagearchitecture** - **x86**、 **x64**、または**ia64**を指定します。</li><li>**Packagelocale** -有効な言語識別子を指定します。 例: **en-us** または **es**</li><li>**パッケージ**: **Yes**または**No**を指定します</li><li>**Packagedatepublished** 済み-日付を YYYY/MM/DD の形式で指定します。</li><li>**Packageversion** -次の形式でバージョンを指定します: a.b.x.y. 例: 6.1.0.0</li><li>**Driverdescription** -任意の文字列値を指定します</li><li>**Drivermanufacturer** -任意の文字列値を指定します</li><li>**DriverHardwareId** -任意の文字列値を指定します。</li><li>**Driver互換 id** -任意の文字列値を指定します</li><li>**Driverexcludeid** -任意の文字列値を指定します</li><li>**Drivergroupid** -有効な GUID を指定してください。 例: {4d36e972-e325-11ce-bfc1-08002be10318}</li><li>**Drivergroupname** -任意の文字列値を指定します</li></ul> これらの値の詳細については、「 [ドライバーとパッケージの属性](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759262(v=ws.11))」を参照してください。 |

## <a name="examples"></a>例

ドライバーグループパッケージを追加するには、次のいずれかを入力します。

```
wdsutil /verbose /add-DriverGroupPackages /DriverGroup:printerdrivers /Filtertype:PackageClass /Operator:Equal /Value:printer /Filtertype:DriverManufacturer /Operator:NotEqual /Value:Name1 /Value:Name2
```

```
wdsutil /verbose /add-DriverGroupPackages /DriverGroup:DisplayDriversX86 /Filtertype:PackageClass /Operator:Equal /Value:Display /Filtertype:PackageArchitecture /Operator:Equal /Value:x86 /Filtertype:Packagedateadded /Operator:LessOrEqual /Value:2008/01/01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil add driverpackage コマンド](wdsutil-add-driverpackage.md)

- [wdsutil add drivergrouppackage コマンド](wdsutil-add-drivergrouppackage.md)

- [wdsutil add alldriverpackages コマンド](wdsutil-add-alldriverpackages.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
