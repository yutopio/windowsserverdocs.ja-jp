---
title: wdsutil add imagedriverpackage
description: Wdsutil add imagedriverpackage コマンドの参照記事。ドライバーストア内のドライバーパッケージをサーバー上の既存のブートイメージに追加します。
ms.topic: reference
ms.assetid: 6c2a4833-6427-47f8-9ffb-20b3786cb406
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5d441007f673a194799e245bb704d31add81a483
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524507"
---
# <a name="wdsutil-add-imagedriverpackage"></a>wdsutil add imagedriverpackage

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバー上の既存のブート イメージにドライバー ストアに含まれるドライバー パッケージを追加します。

## <a name="syntax"></a>構文

```
wdsutil /add-ImageDriverPackage [/Server:<Servername>] [media:<Imagename>] [mediatype:Boot] [/Architecture:{x86 | ia64 | x64}] [/Filename:<Filename>] {/DriverPackage:<Package Name> | /PackageId:<ID>}
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| [メディア: `<Imagename>` ] | ドライバーを追加するイメージの名前を指定します。 |
| [mediatype: ブート] | ドライバーを追加する画像の種類を指定します。 ドライバー パッケージは、ブート イメージにのみ追加できます。 |
| [/アーキテクチャ: `{x86 | ia64 | x64}` ] | ブート イメージのアーキテクチャを指定します。 異なるアーキテクチャのブートイメージで同じイメージ名を持つことができるため、正しいイメージが使用されるようにアーキテクチャを指定する必要があります。 |
| [/ファイル名:`<Filename>`] | ファイルの名前を指定します。 イメージは、名前によって一意に識別できない、ファイル名を指定してください。 |
| [/Driverpackage:`<Name>` | イメージに追加するドライバー パッケージの名前を指定します。 |
| [/パッケージ Id:`<ID>`] | ドライバーパッケージの Windows 展開サービス ID を指定します。 ドライバーパッケージを名前で一意に識別できない場合は、このオプションを指定する必要があります。 パッケージ ID を検索するには、パッケージが含まれているドライバーグループ (または [ **すべてのパッケージ** ] ノード) を選択し、パッケージを右クリックして、[ **プロパティ**] を選択します。 [ **全般** ] タブにパッケージ ID が表示されます。例: {DD098D20-1850-4fc8-8E35-EA24A1BEFF5E}。 |

## <a name="examples"></a>例

ドライバーパッケージをブートイメージに追加するには、次のいずれかを入力します。

```
wdsutil /add-ImageDriverPackagmedia:WinPE Boot Imagemediatype:Boot /Architecture:x86 /DriverPackage:XYZ
```

```
wdsutil /verbose /add-ImageDriverPackagmedia:WinPE Boot Image /Server:MyWDSServemediatype:Boot /Architecture:x64 /PackageId:{4D36E972-E325-11CE-Bfc1-08002BE10318}
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil add imagedriverpackages コマンド](wdsutil-add-imagedriverpackages.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
