---
title: select partition
description: 参照記事 * * * *-
ms.topic: reference
ms.assetid: 25f70083-b8f7-4a8e-9b34-4b3ffbe06670
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 816a235f7ba83320828a5dc72c9f2558c27b2ed8
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027910"
---
# <a name="select-partition"></a>select partition

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定されたパーティションを選択し、そのパーティションにフォーカスを移動します。 このコマンドは、現在フォーカスが、選択したディスクのパーティションを表示することもできます。



## <a name="syntax"></a>構文

```
select partition=<n>
```

### <a name="parameters"></a>パラメーター

|   パラメーター    |                                                                                    説明                                                                                    |
|----------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| partition\=<n> | フォーカスを受け取るパーティションの数。 使用して現在選択されているディスク上のすべてのパーティションの番号を表示する、 **パーティションを一覧表示** diskpart コマンドです。 |

## <a name="remarks"></a>解説

-   使用して、ディスクを選択するパーティションを選択する前にまず必要があります、 **select ディスク** コマンドです。

-   パーティション番号が指定されていない場合、このコマンドは、現在選択されているディスクにフォーカスがあるパーティションを表示します。

-   ボリュームに対応するパーティションが選択されている場合は、パーティションが自動的に選択されます。

-   対応するボリュームを持つパーティションを選択すると、ボリュームが自動的に選択されます。

## <a name="examples"></a>例
フォーカスをパーティション 3 に、次のように入力します。

```
select partitition=3
```

現在フォーカスが、選択したディスクのパーティションを表示するには、次のように入力します。

```
select partition
```

## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)




