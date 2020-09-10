---
title: convert
description: ディスクの種類をディスクから別のディスクに変換する convert コマンドの参照記事です。
ms.topic: reference
ms.assetid: ae151297-af21-4701-bd69-21d775518e03
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 654d5266fff3a3fffadb9d176eb07a792f22fa01
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629272"
---
# <a name="convert"></a>convert

ディスクをディスクの種類別に変換します。

## <a name="syntax"></a>構文

```
convert basic
convert dynamic
convert gpt
convert mbr
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| [基本コマンドの変換](convert-basic.md) | 空のダイナミック ディスクをベーシック ディスクに変換します。 |
| [動的コマンドの変換](convert-dynamic.md) | ベーシック ディスクをダイナミック ディスクに変換します。 |
| [gpt コマンドの変換](convert-gpt.md) | マスター ブート レコード (MBR) パーティション スタイルを持つ空のベーシック ディスクを、GUID パーティション テーブル (GPT) パーティション スタイルを持つベーシック ディスクに変換します。 |
| [mbr コマンドの変換](convert-mbr.md) | GUID パーティションテーブル (GPT) パーティションスタイルを持つ空のベーシックディスクを、マスターブートレコード (MBR) パーティションスタイルを持つベーシックディスクに変換します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
