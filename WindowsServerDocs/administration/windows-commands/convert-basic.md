---
title: convert basic
description: '[基本の変換] コマンドの参照記事では、空のダイナミックディスクをベーシックディスクに変換します。'
ms.topic: reference
ms.assetid: 61329896-3b56-4959-8d58-45cbe18ba860
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 18b5a447a9003b051f398a9943f235d217851fe8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629367"
---
# <a name="convert-basic"></a>convert basic

空のダイナミックディスクをベーシックディスクに変換します。 この操作を成功させるには、ダイナミックディスクを選択する必要があります。 [[ディスクの選択] コマンド](select-disk.md)を使用してダイナミックディスクを選択し、それにフォーカスを移動します。

> [!IMPORTANT]
> ディスクをベーシック ディスクに変換するためには、そのディスクが空である必要があります。 ディスクを変換する前に、データのバックアップをとり、パーティションまたはボリュームをすべて削除してください。

> [!NOTE]
> このコマンドの使用方法については、「 [ダイナミックディスクをベーシックディスクに戻す](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755238(v=ws.11))」を参照してください。

## <a name="syntax"></a>構文

```
convert basic [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>例

選択したダイナミックディスクをベーシックに変換するには、次のように入力します。

```
convert basic
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [convert コマンド](convert.md)
