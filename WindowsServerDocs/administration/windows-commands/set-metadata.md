---
title: set metadata
description: '[メタデータの設定] コマンドの参照記事。シャドウコピーをコンピューター間で転送するために使用するシャドウ作成メタデータファイルの名前と場所を設定します。'
ms.topic: reference
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2ff03661d953ae7afc39117ced89734c5df02c14
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389076"
---
# <a name="set-metadata"></a>set metadata

シャドウ コピーを別の 1 台のコンピューターに転送するために使用したシャドウの作成のメタデータ ファイルの場所と名前を設定します。 パラメーターを指定せずに使用する場合 **メタデータ設定** コマンド プロンプトでヘルプを表示します。

## <a name="syntax"></a>構文

```
set metadata [<drive>:][<path>]<metadata.cab>
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| `[<drive>:][<path>]` | メタデータ ファイルを作成する場所を指定します。 |
| `<metadata.cab>` | シャドウの作成のメタデータを格納する cab ファイルの名前を指定します。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コンテキストコマンドの設定](set-context.md)

- [set option コマンド](set-option.md)

- [詳細コマンドの設定](set-verbose.md)
