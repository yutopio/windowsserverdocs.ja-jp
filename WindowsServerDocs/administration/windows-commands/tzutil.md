---
title: tzutil
description: Windows タイムゾーンユーティリティを表示する、tzutil コマンドの参照記事です。
ms.topic: reference
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8778758c2e3b72827a7dba5844539d27519a19da
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156335"
---
# <a name="tzutil"></a>tzutil

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows タイムゾーンユーティリティを表示します。

## <a name="syntax"></a>構文

```
tzutil [/?] [/g] [/s <timezoneID>[_dstoff]] [/l]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /g | 現在のタイムゾーン ID を表示します。 |
| /s `<timezoneID>[_dstoff]` | 指定されたタイムゾーン ID を使用して、現在のタイムゾーンを設定します。 **_Dstoff**サフィックスは、タイムゾーンの夏時間調整を無効にします (該当する場合)。 値は引用符で囲む必要があります。 |
| /l | 有効なタイムゾーン Id と表示名をすべて一覧表示します。 次のような出力が表示されます。<ul><li>`<display name>`</li><li>`<time zone ID>`</li></ul> |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

終了コード **0** は、コマンドが正常に完了したことを示します。

## <a name="examples"></a>使用例

現在のタイムゾーン ID を表示するには、次のように入力します。

```
tzutil /g
```

現在のタイムゾーンを太平洋標準時に設定するには、次のように入力します。

```
tzutil /s "Pacific Standard time"
```

現在のタイムゾーンを太平洋標準時に設定し、夏時間調整を無効にするには、次のように入力します。

```
tzutil /s "Pacific Standard time_dstoff"
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
