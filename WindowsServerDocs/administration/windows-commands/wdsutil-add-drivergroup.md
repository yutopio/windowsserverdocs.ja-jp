---
title: wdsutil add drivergroup
description: サーバーにドライバーグループを追加する wdsutil add drivergroup コマンドの参照記事です。
ms.topic: reference
ms.assetid: 2a92fe8f-03f9-462a-b99e-f23275259807
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 68583ba35c141df03cbc5e351da6c4dc8ea4e161
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524617"
---
# <a name="wdsutil-add-drivergroup"></a>wdsutil add drivergroup

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバーに、ドライバー グループを追加します。

## <a name="syntax"></a>構文

```
wdsutil /add-DriverGroup /DriverGroup:<Groupname>\n\ [/Server:<Servername>] [/Enabled:{Yes | No}] [/Applicability:{Matched | All}] [/Filtertype:<Filtertype> /Policy:{Include | Exclude} /Value:<Value> [/Value:<Value> ...]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| DriverGroup`<Groupname>` | 新しいドライバー グループの名前を指定します。 |
| Server`<Servername>` | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| Enabled`{Yes|No}` | 有効またはパッケージを無効にします。 |
| 適応性`{Matched|All}` | フィルター条件が満たされた場合は、インストールするパッケージを指定します。 **一致** とは、クライアントのハードウェアに一致するドライバーパッケージのみをインストールすることを意味します。 **すべて** 手段は、クライアントのハードウェアに関係なくすべてのパッケージをインストールします。 |
| Filtertype`<Filtertype>` | グループに追加するフィルターの種類を指定します。 1 つのコマンドでは、複数のフィルターの種類を指定できます。 各フィルターの種類は続けてください **/policy:enabled** と 1 つ以上 **/value**します。 有効な値は、次のとおりです。<ul><li>BiosVendor</li><li>Bios のバージョン</li><li>Chassistype</li><li>Manufacturer</li><li>Uuid</li><li>Osversion</li><li>Osedition</li><li>OsLanguage</li></ul> 他のすべてのフィルターの種類の値を取得する方法については、「 [ドライバーグループのフィルター](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759191(v=ws.11))」を参照してください。 |
| [/ポリシー: `{Include|Exclude}` ] | フィルターを設定するポリシーを指定します。 場合 **/policy:enabled** に設定されている **Include**, 、フィルターに一致するクライアント コンピューターがこのグループのドライバーをインストールを許可します。 場合 **/policy:enabled** に設定されている **除外**, 、このグループのドライバーをインストールするフィルターに一致するクライアント コンピューターは許可されません。 |
| [/Value:`<Value>`] | **/Filtertype**に対応するクライアントの値を指定します。 1 つの型に複数の値を指定できます。 許容されるフィルターの種類の値については、「 [ドライバーグループのフィルター](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd759191(v=ws.11))」を参照してください。 |

## <a name="examples"></a>例

ドライバーグループを追加するには、次のいずれかを入力します。

```
wdsutil /add-DriverGroup /DriverGroup:printerdrivers /Enabled:Yes
```

```
wdsutil /add-DriverGroup /DriverGroup:printerdrivers /Applicability:All /Filtertype:Manufacturer /Policy:Include /Value:Name1 /Filtertype:Chassistype /Policy:Exclude /Value:Tower /Value:MiniTower
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil add drivergrouppackage コマンド](wdsutil-add-drivergrouppackage.md)

- [wdsutil add drivergrouppackages コマンド](wdsutil-add-drivergrouppackages.md)

- [wdsutil add drivergroupfilter コマンド](wdsutil-add-drivergroupfilter.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
