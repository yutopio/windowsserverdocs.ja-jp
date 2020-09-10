---
title: exec
description: ローカルコンピューター上でスクリプトファイルを実行する exec コマンドの参照記事です。
ms.topic: reference
ms.assetid: 364e8baf-576f-401b-a431-7d3c06621614
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 668dc3cf3d93d11066d7dece4309f586b3a5b964
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635961"
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
