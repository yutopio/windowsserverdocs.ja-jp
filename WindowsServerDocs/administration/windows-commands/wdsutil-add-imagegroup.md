---
title: wdsutil 追加-imagegroup
description: Windows 展開サービスサーバーにイメージグループを追加する、wdsutil add imagegroup コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 6ca88671-51de-4924-b969-88f3dfd84270
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3bffb562ba019bb55c783541b78c906dd4a08dc7
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524467"
---
# <a name="wdsutil-add-imagegroup"></a>wdsutil 追加-imagegroup

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービス サーバーには、イメージ グループを追加します。

## <a name="syntax"></a>構文

```
wdsutil [Options] /add-ImageGroup imageGroup:<Imagegroupname> [/Server:<Server name>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| imageGroup: `<Imagegroupname>` ] | 追加するイメージの名前を指定します。 |
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |

## <a name="examples"></a>例

イメージグループを追加するには、次のいずれかを入力します。

```
wdsutil /add-ImageGroup imageGroup:ImageGroup2
```

```
wdsutil /verbose /add-Imagegroup imageGroup:My Image Group /Server:MyWDSServer
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil get-allimagegroups コマンド](wdsutil-get-allimagegroups.md)

- [wdsutil get imagegroup コマンド](wdsutil-get-imagegroup.md)

- [wdsutil remove-imagegroup コマンド](wdsutil-remove-imagegroup.md)

- [wdsutil set-imagegroup コマンド](wdsutil-set-imagegroup.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
