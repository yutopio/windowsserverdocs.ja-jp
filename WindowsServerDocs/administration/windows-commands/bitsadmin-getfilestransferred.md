---
title: bitsadmin getfilestransferred
description: Bitsadmin getfilestransferred コマンドの参照記事。指定されたジョブで転送されたファイルの数を取得します。
ms.topic: reference
ms.assetid: e282815c-938b-4ac0-a09d-9baafb656dcb
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e86e35d80e8e6b00d973b60e314f22068f7d115b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033590"
---
# <a name="bitsadmin-getfilestransferred"></a>bitsadmin getfilestransferred

指定したジョブで転送されたファイルの数を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getfilestransferred <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
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
