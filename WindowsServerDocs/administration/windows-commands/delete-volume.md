---
title: delete volume
description: ボリュームの削除コマンドの参照記事。選択されたボリュームを削除します。
ms.topic: reference
ms.assetid: f625933d-0f47-409e-93b2-a3e234049a5d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 66793e9d7c22b337164807bf76ee82c10d70547c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628800"
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

| パラメーター | Description |
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