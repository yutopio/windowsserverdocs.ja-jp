---
title: bitsadmin getfilestransferred
description: Bitsadmin getfilestransferred コマンドの参照記事。指定されたジョブで転送されたファイルの数を取得します。
ms.topic: reference
ms.assetid: e282815c-938b-4ac0-a09d-9baafb656dcb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b4a34e799b2d7e41373a1b4682c77e3ad93d36c2
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632098"
---
# <a name="bitsadmin-getfilestransferred"></a>bitsadmin getfilestransferred

指定したジョブで転送されたファイルの数を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getfilestransferred <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブで転送されたファイルの数を取得するには、次のようにします。

```
bitsadmin /getfilestransferred myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
