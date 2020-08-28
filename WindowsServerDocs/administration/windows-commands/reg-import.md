---
title: reg import
description: Reg import コマンドの参照記事。エクスポートされたレジストリサブキー、エントリ、および値を含むファイルの内容をローカルコンピューターのレジストリにコピーします。
ms.topic: reference
ms.assetid: 0be103de-08fc-4f02-b590-361782680b3e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 4da7e3c66bedd3ba6a85e64c69e3fc4866df1e6c
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028040"
---
# <a name="reg-import"></a>reg import

コピーを含むファイルの内容は、ローカル コンピューターのレジストリにレジストリ キー、エントリ、および値をエクスポートします。

## <a name="syntax"></a>構文

```
reg import <filename>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<filename>` | ローカル コンピューターのレジストリにコピーされるコンテンツを含むファイルのパスと名前を指定します。 使用してこのファイルを事前に作成する必要があります **reg エクスポート**します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- **Reg インポート**操作の戻り値は次のとおりです。

    | [値] | 説明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 障害 |

### <a name="examples"></a>例

レジストリ エントリ AppBkUp.reg という名前のファイルからをインポートするには、次のように入力します。

```
reg import AppBkUp.reg
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [reg export コマンド](reg-export.md)
