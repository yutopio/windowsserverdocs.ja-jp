---
title: bitsadmin sethttpmethod
description: Bitsadmin sethttpmethod コマンドの参照記事。使用する HTTP 動詞を設定します。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 0c8d2357e35831db89365eabbe0b97cdec88b6aa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630876"
---
# <a name="bitsadmin-sethttpmethod"></a>bitsadmin sethttpmethod

使用する HTTP 動詞を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /sethttpmethod <job> <httpmethod>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| httpmethod | 使用する HTTP 動詞。 使用可能な動詞の詳細については、「 [メソッドの定義](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)」を参照してください。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
