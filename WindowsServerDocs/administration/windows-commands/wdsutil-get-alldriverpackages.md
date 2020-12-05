---
title: wdsutil get alldriverpackages
description: Wdsutil get alldriverpackages コマンドのリファレンス記事。指定された検索条件に一致するサーバー上のすべてのドライバーパッケージに関する情報を表示します。
ms.topic: reference
ms.assetid: 9eb8fcb7-ef46-4c8d-9623-8969a3c8b8a4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: dd144d9abc2776f7e56913efd40775c1eef4d3ac
ms.sourcegitcommit: 28b5ab74cb0b40539ccc1a83998d6391e87fe51f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96614924"
---
# <a name="wdsutil-get-alldriverpackages"></a>wdsutil get alldriverpackages

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定した検索条件に一致するサーバー上のすべてのドライバー パッケージについての情報を表示します。

## <a name="syntax"></a>構文

```
wdsutil /get-alldriverpackages [/server:<servername>] [/show:{drivers | files | all}] [/filtertype:<filtertype> /operator:{equal | notequal | greaterorequal | lessorequal | contains} /value:<value> [/value:<value> ...]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `[/server:<servername>] `| サーバーの名前。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカルサーバーが使用されます。 |
| `[/show:{drivers | files | all}]` | パッケージ情報を表示することを示します。 **/Show** が指定されていない場合、既定では、ドライバーパッケージのメタデータのみが返されます。 **ドライバー** によってパッケージ内のドライバーの一覧が表示され、 **ファイル** にはパッケージ内のファイルの一覧が表示され、 **すべて** のドライバーとファイルが表示されます。 |
| `/filtertype:<filtertype>` | 検索するドライバー パッケージの属性を指定します。 1 つのコマンドでは、複数の属性を指定できます。 また、このオプションを使用して、 **/演算子** と **/値** を指定する必要があります。<p>には、 `<filtertype>` 次のいずれかを指定できます。<ul><li>PackageId</li><li>PackageName</li><li>PackageEnabled</li><li>Packagedateadded</li><li>PackageInfFilename</li><li>PackageClass</li><li>PackageProvider</li><li>PackageArchitecture</li><li>PackageLocale</li><li>PackageSigned</li><li>PackagedatePublished 済み</li><li>Packageversion</li><li>Driverdescription</li><li>DriverManufacturer</li><li>DriverHardwareId</li><li>Driver互換 Id</li><li>DriverGroupId</li><li>DriverGroupName</li></ul> |
| `/operator:{equal | notequal | greaterorequal | lessorequal | contains}` | 属性と値間のリレーションシップを指定します。 **Contains** は、文字列属性でのみ指定できます。 **Greaterorequal** および **不等号** を指定することができます日付とバージョンの属性です。 |
| `/value:<value>` | 指定した検索する値を指定 `<attribute>`します。 1つの **/filtertype** に対して複数の値を指定できます。 次の一覧では、各フィルターに指定できる属性について説明します。 これらの属性の詳細については、「 [ドライバーとパッケージの属性](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759262(v=ws.11))」を参照してください。 属性には次のものが含まれます。<ul><li>**PackageId.** 有効な GUID を指定します。 例: {4d36e972-e325-11ce-bfc1-08002be10318}。</li><li>**PackageName.** 任意の文字列値を指定します。</li><li>**PackageEnabled。** *Yes* または *No* を指定します。</li><li>**Packagedateadded。** 次の形式で日付を指定します: YYYY/MM/DD</li><li>**PackageInfFilename。** 任意の文字列値を指定します。</li><li>**パッケージの Eclass。** 有効なクラス名またはクラス GUID を指定します。 例: *DiskDrive*、 *Net*、 *{4d36e972-e325-11ce-bfc1-08002be10318}*。</li><li>**Install-packageprovider.** 任意の文字列値を指定します。</li><li>**PackageArchitecture.** *X86*、 *x64*、または *ia64* を指定します。</li><li>**パッケージのロケール。** 有効な言語識別子を指定します。 例: *EN-US* または *ES-ES* します。</li><li>**パッケージ。** **Yes** または **No** を指定します。</li><li>**PackagedatePublished されました。** 次の形式で日付を指定します: YYYY/MM/DD。</li><li>**Packageversion.** 次の形式でバージョンを指定します: a.b.x.y. 例: 6.1.0.0。</li><li>**Driverdescription。** 任意の文字列値を指定します。</li><li>**DriverManufacturer。** 任意の文字列値を指定します。</li><li>**DriverHardwareId.** 任意の文字列値を指定します。</li><li>**Driver互換 Id。** 任意の文字列値を指定します。</li><li>**DriverExcludeId.** 任意の文字列値を指定します。</li><li>**DriverGroupId.** 有効な GUID を指定します。 例: {4d36e972-e325-11ce-bfc1-08002be10318} します。</li><li>**DriverGroupName。** 任意の文字列値を指定します。</li></ul> |

## <a name="examples"></a>例

情報を表示するには、次のいずれかを入力します。

```
wdsutil /get-alldriverpackages /server:MyWdsServer /show:all /filtertype:drivergroupname /operator:contains /value:printer /filtertype:packagearchitecture /operator:equal /value:x64 /value:x86
```

```
wdsutil /get-alldriverpackages /show:drivers /filtertype:packagedateadded /operator:greaterorequal /value:2008/01/01
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil get driverpackage コマンド](wdsutil-get-driverpackage.md)

- [wdsutil get driverpackagefile コマンド](wdsutil-get-driverpackagefile.md)
