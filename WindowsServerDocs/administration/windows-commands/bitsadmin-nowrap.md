---
title: bitsadmin nowrap
description: Bitsadmin nowrap コマンドの参照記事。コマンドウィンドウの右端からはみ出た出力テキストの行をすべて切り捨てます。
ms.topic: reference
ms.assetid: 85a47b90-783a-41e4-96f2-81f26ae8ca93
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2e5724f3dedb808898cd070026e2e4a944d4731b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631423"
---
# <a name="bitsadmin-nowrap"></a>bitsadmin nowrap

コマンドウィンドウの右端を超えて拡張する出力テキストの行をすべて切り捨てます。 既定では、 **モニター** スイッチを除くすべてのスイッチが出力をラップします。 他のスイッチの前に、 **nowrap** スイッチを指定します。

## <a name="syntax"></a>構文

```
bitsadmin /nowrap
```

## <a name="examples"></a>例

出力をラップせずに *Mydownloadjob* という名前のジョブの状態を取得するには、次のようにします。

```
bitsadmin /nowrap /getstate myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
