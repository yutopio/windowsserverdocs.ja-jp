---
title: wdsutil get alldrivergroups
description: サーバー上のすべてのドライバーグループに関する情報を表示する、wdsutil get alldrivergroups コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: f245ba53-f150-41b1-8418-38dcf0410a05
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b6d407e91af9132d6d2bc87ccb86320e3fe42b76
ms.sourcegitcommit: 28b5ab74cb0b40539ccc1a83998d6391e87fe51f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96614944"
---
# <a name="wdsutil-get-alldrivergroups"></a>wdsutil get alldrivergroups

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバー上のすべてのドライバー グループに関する情報を表示します。

## <a name="syntax"></a>構文

```
wdsutil /get-alldrivergroups [/server:<servername>] [/show:{packagemetadata | filters | all}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `[/server:<servername>]` | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| `/show:{packagemetadata | filters | all}]` | 指定したグループ内のすべてのドライバー パッケージのメタデータを表示します。 **行き着きます** ドライバー グループのすべてのフィルターに関する情報を表示します。 **フィルター** すべてのドライバー パッケージのメタデータと、グループのフィルターが表示されます。 |

## <a name="examples"></a>例

ドライバーファイルに関する情報を表示するには、次のいずれかを入力します。

```
wdsutil /get-alldrivergroups /server:MyWdsServer /show:All
```

```
wdsutil /get-alldrivergroups [/show:packagemetadata]
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-
- [wdsutil get drivergroup コマンド](wdsutil-get-drivergroup.md)
