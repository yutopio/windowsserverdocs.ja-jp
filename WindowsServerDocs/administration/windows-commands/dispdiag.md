---
title: dispdiag
description: 表示情報をファイルに記録する dispdiag コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 5079e1dd-b57c-44ed-970f-e6b409369e03
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 92dd0b49d8907f3ec934fd59d61b0504b622e80b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89030840"
---
# <a name="dispdiag"></a>dispdiag

ログには、ファイルの情報が表示されます。

## <a name="syntax"></a>構文

```
dispdiag [-testacpi] [-d] [-delay <seconds>] [-out <filepath>]
```

#### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| -testacpi | ホットキー診断テストを実行します。 テスト中に押されたキーのキー名、コード、およびスキャンコードを表示します。 |
| -d | テスト結果と共にダンプファイルを生成します。 |
| -delay `<seconds>` | 指定された時間 *(秒単位)* でデータの収集を遅らせます。 |
| -out `<filepath>`  | 収集したデータを保存するパスとファイル名を指定します。 これは、最後のパラメーターである必要があります。 |
| -? | 使用可能なコマンドパラメーターを表示し、それらを使用するためのヘルプを提供します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
