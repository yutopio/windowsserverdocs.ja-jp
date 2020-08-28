---
title: bitsadmin cache および info
description: 特定のキャッシュエントリをダンプする bitsadmin cache と info コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 15975cbf-dba6-49ca-a725-d15ce1952de5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: cce96d25b3968c1f975b6426ce8c25e7420f7bd3
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028890"
---
# <a name="bitsadmin-cache-and-info"></a>bitsadmin cache および info

特定のキャッシュエントリをダンプします。

## <a name="syntax"></a>構文

```
bitsadmin /cache /info recordID [/verbose]
```

### <a name="parameters"></a>パラメーター

| Paramreter | 説明 |
| -------------- | -------------- |
| recordID | キャッシュエントリに関連付けられている GUID。 |

## <a name="examples"></a>例

RecordID の値 {6511FB02-E195-40A2-B595-E8E2F8F47702} を使用してキャッシュエントリをダンプするには、次のように入力します。

```
bitsadmin /cache /info {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin cache コマンド](bitsadmin-cache.md)
