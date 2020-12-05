---
title: wdsutil get-allimagegroups
description: Wdsutil get allimagegroups コマンドのリファレンス記事。サーバー上のすべてのイメージグループとそれらのイメージグループ内のすべてのイメージに関する情報を取得します。
ms.topic: reference
ms.assetid: 2ca06533-bcf5-4590-ac8e-263d6c9874f8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7209b0f806b0fd86167e8fbcf36f717a0d069195
ms.sourcegitcommit: 28b5ab74cb0b40539ccc1a83998d6391e87fe51f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96614864"
---
# <a name="wdsutil-get-allimagegroups"></a>wdsutil get-allimagegroups

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバーおよびそれらのイメージ グループのすべてのイメージ上のすべてのイメージ グループに関する情報を取得します。

## <a name="syntax"></a>構文

```
wdsutil [options] /get-allimagegroups [/server:<servername>] [/detailed]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `[/server:<servername>]` | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| 詳細/ | 各イメージからイメージのメタデータを返します。 このパラメーターを使用しない場合、既定の動作では、各イメージのイメージ名、説明、およびファイル名のみが返されます。 |

## <a name="examples"></a>例

イメージグループに関する情報を表示するには、次のいずれかを入力します。

```
wdsutil /get-allimagegroups
```

```
wdsutil /verbose /get-allimagegroups /server:MyWDSServer /detailed
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil add imagegroup コマンド](wdsutil-add-imagegroup.md)

- [wdsutil remove-imagegroup コマンド](wdsutil-remove-imagegroup.md)

- [wdsutil set-imagegroup コマンド](wdsutil-set-imagegroup.md)
