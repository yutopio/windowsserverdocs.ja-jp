---
title: retain
description: '[保持] コマンドの参照記事。ブートボリュームまたはシステムボリュームとして使用する既存のダイナミックボリュームを準備します。'
ms.topic: reference
ms.assetid: eeab0aef-2ba5-441a-a10d-bbef6f0d7e3e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 201aa8b79f8ac0f89d44be7db3f84c9f3059e206
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626904"
---
# <a name="retain"></a>retain

ブートボリュームまたはシステムボリュームとして使用するために、既存のシンプルなダイナミックボリュームを準備します。 マスターブートレコード (MBR) ダイナミックディスクを使用する場合、このコマンドはマスターブートレコードにパーティションエントリを作成します。 GUID パーティションテーブル (GPT) ダイナミックディスクを使用する場合、このコマンドは GUID パーティションテーブルにパーティションエントリを作成します。

## <a name="syntax"></a>Syntax

```
retain
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
