---
title: diskpart のインポート
description: インポートコマンドの参照記事。外部ディスクグループをローカルコンピューターのディスクグループにインポートします。
ms.topic: reference
ms.assetid: 4b9d2751-7637-4738-83b0-8c578eb28f27
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1a6bbd2a2adb6017f67667e7e2e71b0f6302b517
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037990"
---
# <a name="import-diskpart"></a>import (diskpart)

外部ディスクグループをローカルコンピューターのディスクグループにインポートします。 このコマンドは、フォーカスがあるディスクと同じグループにあるすべてのディスクをインポートします。

> :このコマンドを使用する前に、 [[ディスクの選択] コマンド](select-disk.md) を使用して、外部ディスクグループ内のダイナミックディスクを選択し、そのディスクにフォーカスを移動する必要があります。

## <a name="syntax"></a>構文

```
import [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

### <a name="examples"></a>例

ローカルコンピューターのディスクグループにフォーカスがあるディスクと同じディスクグループにあるすべてのディスクをインポートするには、次のように入力します。

```
import
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [diskpart コマンド](diskpart.md)
