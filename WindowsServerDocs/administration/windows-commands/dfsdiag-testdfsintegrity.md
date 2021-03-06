---
title: dfsdiag testdfsintegrity
description: 分散ファイルシステム (DFS) 名前空間の整合性をチェックする、DFS diag testdfsintegrity コマンドの参照記事。
ms.topic: reference
ms.assetid: 173ee832-26e1-4ec8-a23a-38a7d6229ac3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4aa6eb44084ec939ebed708982e527b237d407c7
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634151"
---
# <a name="dfsdiag-testdfsintegrity"></a>dfsdiag testdfsintegrity

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

次のテストを実行して、分散ファイルシステム (DFS) 名前空間の整合性をチェックします。

- DFS メタデータの破損またはドメインコントローラー間の不整合を確認します。

- アクセスベースの列挙の構成を検証して、DFS メタデータと名前空間サーバー共有の間で一貫性があることを確認します。

- 重複する DFS フォルダー (リンク)、重複するフォルダー、フォルダーターゲットが重複するフォルダーを検出します。

## <a name="syntax"></a>構文

```
dfsdiag /testdfsintegrity /DFSroot: <DFS root path> [/recurse] [/full]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| /Dfs ルート: `<DFS root path>` | 診断する DFS 名前空間。 |
| /recurse | 名前空間の interlinks を含め、テストを実行します。 |
| /full | 共有および NTFS Acl の一貫性と、すべてのフォルダーターゲットのクライアント側の構成を確認します。 また、online プロパティが設定されていることを確認します。 |

## <a name="examples"></a>例

相互リンクを含め、 *com\MyNamespace*の分散ファイルシステム (DFS) 名前空間の整合性と整合性を確認するには、次のように入力します。

```
dfsdiag /testdfsintegrity /DFSRoot:\contoso.com\MyNamespace /recurse /full
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [dfsdiag コマンド](dfsdiag.md)
