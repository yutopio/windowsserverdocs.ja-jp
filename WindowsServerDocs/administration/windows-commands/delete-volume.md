---
title: delete volume
description: ボリュームの削除コマンドの参照記事。選択されたボリュームを削除します。
ms.topic: reference
ms.assetid: f625933d-0f47-409e-93b2-a3e234049a5d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7c88834b800414bcf3ff246272ec187fb98d47db
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024156"
---
# <a name="delete-volume"></a>delete volume

選択されたボリュームを削除します。 開始する前に、この操作を成功させるボリュームを選択する必要があります。 使用して、 [ボリュームを選択して](select-volume.md) コマンドのボリュームを選択し、それにフォーカスをします。

> [!IMPORTANT]
> システムボリューム、ブートボリューム、またはアクティブなページングファイルまたはクラッシュダンプ (メモリダンプ) を含むボリュームを削除することはできません。

## <a name="syntax"></a>構文

```
delete volume [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>例

フォーカスがあるボリュームを削除するには、次のように入力します。

```
delete volume
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [select volume](select-volume.md)

- [delete コマンド](delete.md)