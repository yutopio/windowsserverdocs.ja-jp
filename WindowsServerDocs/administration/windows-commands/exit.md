---
title: exit
description: コマンドインタープリターを終了する終了の参照記事です。
ms.topic: reference
ms.assetid: d3cee4a2-6210-46f0-b8e4-7381c3c4e530
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9e065a25f339a093492a05102b10455b11da5ecb
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89035860"
---
# <a name="exit"></a>exit

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

コマンドインタープリターまたは現在のバッチスクリプトを終了します。

## <a name="syntax"></a>構文

```
exit [/b] [<exitcode>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| /b | Cmd.exe を終了するのではなく、現在のバッチスクリプトを終了します。 バッチスクリプトの外部から実行された場合は、Cmd.exe 終了します。 |
| `<exitcode>` | 数値を指定します。 **/B**が指定されている場合、ERRORLEVEL 環境変数はその数値に設定されます。 コマンドインタープリターを終了すると、プロセス終了コードはその番号に設定されます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

コマンドインタープリターを閉じるには、次のように入力します。

```
exit
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
