---
title: exec
description: ローカルコンピューター上でスクリプトファイルを実行する exec コマンドの参照記事です。
ms.topic: reference
ms.assetid: 364e8baf-576f-401b-a431-7d3c06621614
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: e0e4cd876fe5c6abcf909f20e330ff347db1113b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023996"
---
# <a name="exec"></a>exec

ローカルコンピューター上でスクリプトファイルを実行します。 このコマンドでは、バックアップまたは復元シーケンスの一部としてデータの複製または復元も実行されます。 スクリプトが失敗した場合は、エラーが返され、DiskShadow が終了します。

このファイルは、 **cmd** スクリプトにすることができます。

## <a name="syntax"></a>構文

```
exec <scriptfile.cmd>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<scriptfile.cmd>` | 実行するスクリプトファイルを指定します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [diskshadow コマンド](diskshadow.md)
