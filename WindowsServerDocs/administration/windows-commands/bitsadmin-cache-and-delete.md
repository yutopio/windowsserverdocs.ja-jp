---
title: bitsadmin cache および delete
description: 特定のキャッシュエントリを削除する bitsadmin cache と delete コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 22540273-55a5-46ea-869b-6df2aa6808a1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3dd83b05b0b4964fe8dbaa52a03a651153d9a94d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632648"
---
# <a name="bitsadmin-cache-and-delete"></a>bitsadmin cache および delete

特定のキャッシュエントリを削除します。

## <a name="syntax"></a>構文

```
bitsadmin /cache /delete recordID
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| recordID | キャッシュエントリに関連付けられている GUID。 |

## <a name="examples"></a>例

{6511FB02-E195-40A2-B595-E8E2F8F47702} の RecordID を使用してキャッシュエントリを削除するには、次のように入力します。

```
bitsadmin /cache /delete {6511FB02-E195-40A2-B595-E8E2F8F47702}
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin cache コマンド](bitsadmin-cache.md)
