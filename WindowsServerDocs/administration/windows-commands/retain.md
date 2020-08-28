---
title: retain
description: '[保持] コマンドの参照記事。ブートボリュームまたはシステムボリュームとして使用する既存のダイナミックボリュームを準備します。'
ms.topic: reference
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 98c27c62ab7e0ac3320986dde6049be40d10db57
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036991"
---
# <a name="retain"></a>retain

ブートボリュームまたはシステムボリュームとして使用するために、既存のシンプルなダイナミックボリュームを準備します。 マスターブートレコード (MBR) ダイナミックディスクを使用する場合、このコマンドはマスターブートレコードにパーティションエントリを作成します。 GUID パーティションテーブル (GPT) ダイナミックディスクを使用する場合、このコマンドは GUID パーティションテーブルにパーティションエントリを作成します。

## <a name="syntax"></a>構文

```
retain
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
