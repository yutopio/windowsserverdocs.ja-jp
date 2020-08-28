---
title: tzutil
description: Windows タイムゾーンユーティリティを表示する tzutil のリファレンス記事です。
ms.topic: reference
ms.assetid: bcf6e007-c9b6-4df5-83c5-ed7b4b1b5913
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1d8eae64faf58d404c49afa5b469c61d44807ae0
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89029940"
---
# <a name="tzutil"></a>tzutil

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows タイムゾーンユーティリティを表示します。

## <a name="syntax"></a>構文
```
tzutil [/?] [/g] [/s <timeZoneID>[_dstoff]] [/l]
```
#### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|/?|コマンド プロンプトにヘルプを表示します。|
|/g|現在のタイムゾーン ID を表示します。|
|/s \<timeZoneID> [_dstoff]|指定されたタイムゾーン ID を使用して、現在のタイムゾーンを設定します。 **_Dstoff**サフィックスは、タイムゾーンの夏時間調整を無効にします (該当する場合)。|
|/l|有効なタイムゾーン Id と表示名をすべて一覧表示します。 次のように出力されます。<p>-   \<display name><br />-   \<time zone ID>|

## <a name="remarks"></a>解説
終了コード **0** は、コマンドが正常に完了したことを示します。

## <a name="examples"></a>例
現在のタイムゾーン ID を表示するには、次のように入力します。
```
tzutil /g
```
現在のタイムゾーンを太平洋標準時に設定するには、次のように入力します。
```
tzutil /s Pacific Standard time
```
現在のタイムゾーンを太平洋標準時に設定し、夏時間調整を無効にするには、次のように入力します。
```
tzutil /s Pacific Standard time_dstoff
```
## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)

