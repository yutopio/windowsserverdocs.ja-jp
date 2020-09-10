---
title: dfsdiag testsites
description: Dfs diag testsites の参照記事。名前空間サーバーまたはフォルダー (リンク) のターゲットとして機能するサーバーがすべてのドメインコントローラー上で同じサイトの関連付けを持つことを確認することで、active directory ドメインサービス (AD DS) サイトの構成を確認します。
ms.topic: reference
ms.assetid: 39a0d415-7eb7-4a26-861b-7ff00c45dcda
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c4c1b2eb578245b3d5f1ece443a78e9c0c00372b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634324"
---
# <a name="dfsdiag-testsites"></a>dfsdiag testsites

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

名前空間サーバーまたはフォルダー (リンク) のターゲットとして機能するサーバーがすべてのドメインコントローラー上で同じサイトの関連付けを持つことを確認して、active directory ドメインサービス (AD DS) サイトの構成を確認します。

## <a name="syntax"></a>構文

```
dfsdiag /testsites </machine:<server name>| /DFSpath:<namespace root or DFS folder> [/recurse]> [/full]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `/machine:<server name>` | サイトの関連付けを確認するサーバーの名前。 |
| `/DFSpath:<namespace root or DFS folder>` | サイトの関連付けを検証するターゲットを持つ名前空間のルートまたは分散ファイルシステム (DFS) フォルダー (リンク)。 |
| /recurse | 指定した名前空間のルートにあるすべてのフォルダーターゲットのサイトの関連付けを列挙し、検証します。 |
| /full | AD DS とサーバーのレジストリに同じサイトの関連付け情報が含まれていることを確認します。 |

## <a name="examples"></a>例

*Machine\MyServer*上のサイトの関連付けを確認するには、次のように入力します。

```
dfsdiag /testsites /machine:MyServer
```

分散ファイルシステム (DFS) フォルダーでサイトの関連付けを確認するには、AD DS とサーバーのレジストリに同じサイトの関連付け情報が含まれていることを確認するには、次のように入力します。

```
dfsdiag /TestSites /DFSpath:\\contoso.com\namespace1\folder1 /full
```

名前空間のルートでサイトの関連付けを確認するには、指定した名前空間のルートにあるすべてのフォルダーターゲットのサイトの関連付けを列挙して検証し、AD DS とサーバーのレジストリに同じサイトの関連付け情報が含まれていることを確認するには、次のように入力します。

```
dfsdiag /testsites /DFSpath:\\contoso.com\namespace2 /recurse /full
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [dfsdiag コマンド](dfsdiag.md)
