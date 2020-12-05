---
title: wdsutil get-allimages
description: サーバー上のすべてのイメージに関する情報を取得する、wdsutil get allimages コマンドの参照記事。
ms.topic: reference
ms.assetid: 19de3720-4315-415a-8dc6-486caa0b2100
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2fe93036c5493baed122fede4b25b71349996536
ms.sourcegitcommit: 28b5ab74cb0b40539ccc1a83998d6391e87fe51f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96614934"
---
# <a name="wdsutil-get-allimages"></a>wdsutil get-allimages

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバー上のすべてのイメージに関する情報を取得します。

## <a name="syntax"></a>構文

```
wdsutil /get-allimages [/server:<servername>] /show:{boot | install | legacyris | all} [/detailed]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `[/server:<servername>]` | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| `/show:{boot | install | legacyris | all}` | ブートでブートイメージのみ **が返される** 場合、 **install** はインストールイメージとそのイメージを含むイメージグループに関する情報を返し、 **LegacyRis** はリモートインストールサービス (RIS) イメージのみを返し、 **すべて** のブートイメージ情報、インストールイメージ情報 (イメージグループに関する情報を含む)、および RIS イメージ情報を返します。 |
| 詳細/ | 各イメージからすべてのイメージのメタデータを返すことを示します。 このオプションを使用しない場合、既定の動作は、イメージの名前、説明、およびファイル名のみを返すには。 |

## <a name="examples"></a>例

イメージに関する情報を表示するには、次のいずれかを入力します。

```
wdsutil /get-allimages /show:install
```

```
wdsutil /verbose /get-allimages /server:MyWDSServer /show:all /detailed
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil のイメージの追加コマンド](wdsutil-add-image.md)

- [wdsutil コピー-イメージコマンド](wdsutil-copy-image.md)

- [wdsutil export-イメージコマンド](wdsutil-export-image.md)

- [wdsutil 削除-イメージコマンド](wdsutil-remove-image.md)

- [wdsutil replace-イメージコマンド](wdsutil-replace-image.md)

- [wdsutil set-image コマンド](wdsutil-set-image.md)
