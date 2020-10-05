---
title: サブコマンドの設定-DriverPackage
description: サブコマンド set DriverPackage のリファレンス記事。サーバー上のドライバーパッケージの名前を変更するか、有効または無効にします。
ms.topic: reference
ms.assetid: 11804bb6-ca29-4461-8c63-5131748cd742
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a4b0b3154f6cc7cee34e6fdcc91f332295164541
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731306"
---
# <a name="subcommand-set-driverpackage"></a>サブコマンド: セット DriverPackage

サーバー上のドライバーパッケージの名前を変更するか、有効または無効にします。

## <a name="syntax"></a>構文

```
WDSUTIL /Set-DriverPackage [/Server:<Server name>] {/DriverPackage:<Name> | /PackageId:<ID>} [/Name:<New Name>] [/Enabled:{Yes | No}
```

### <a name="parameters"></a>パラメーター

|        パラメーター         |                                                                                                                                                                                                               説明                                                                                                                                                                                                                |
|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [/Server:\<Server name>] |                                                                                                                                                 サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。                                                                                                                                                 |
| [/DriverPackage:\<Name>] |                                                                                                                                                                                       変更するドライバーパッケージの現在の名前を指定します。                                                                                                                                                                                        |
|    [/パッケージ Id:\<ID>]    | ドライバーパッケージの Windows 展開サービス ID を指定します。 ドライバー パッケージを名前によって一意に識別できない場合は、このオプションを指定する必要があります。 パッケージのこの ID を検索するには、パッケージが含まれているドライバーグループ (または [ **すべてのパッケージ** ] ノード) をクリックし、パッケージを右クリックして、[ **プロパティ**] をクリックします。 [ **全般** ] タブにパッケージ ID が表示されます。例: {DD098D20-1850-4FC8-8E35-EA24A1BEFF5E}。 |
|   [/Name:\<New Name>]    |                                                                                                                                                                                              ドライバーパッケージの新しい名前を指定します。                                                                                                                                                                                              |
|      [/有効: {はい]      |                                                                                                                                                                                                                   番号                                                                                                                                                                                                                    |

## <a name="examples"></a>例

パッケージに関する設定を変更するには、次のいずれかを入力します。
```
WDSUTIL /Set-DriverPackage /PackageId:{4D36E972-E325-11CE-BFC1-08002BE10318} /Name:MyDriverPackage
```
```
WDSUTIL /Set-DriverPackage /DriverPackage:MyDriverPackage /Name:NewName /Enabled:Yes
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)