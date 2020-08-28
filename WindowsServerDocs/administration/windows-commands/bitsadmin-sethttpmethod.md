---
title: bitsadmin sethttpmethod
description: Bitsadmin sethttpmethod コマンドの参照記事。使用する HTTP 動詞を設定します。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 8374a8e306f88cbdbad079d99233171712cc00bc
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026270"
---
# <a name="bitsadmin-sethttpmethod"></a>bitsadmin sethttpmethod

使用する HTTP 動詞を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /sethttpmethod <job> <httpmethod>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| httpmethod | 使用する HTTP 動詞。 使用可能な動詞の詳細については、「 [メソッドの定義](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html)」を参照してください。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
