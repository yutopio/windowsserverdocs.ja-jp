---
title: convert dynamic
description: ベーシックディスクをダイナミックディスクに変換する [動的変換] コマンドの参照記事です。
ms.topic: reference
ms.assetid: 7b8fa4b1-850f-4e48-b05f-871c883ea33c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7a67b7e900ce57e7551d8c565022aa80be5d714a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629350"
---
# <a name="convert-dynamic"></a>convert dynamic

ベーシック ディスクをダイナミック ディスクに変換します。 この操作を成功させるには、ベーシックディスクを選択する必要があります。 [[ディスクの選択] コマンド](select-disk.md)を使用してベーシックディスクを選択し、それにフォーカスを移動します。

> [!NOTE]
> このコマンドの使用方法については、「 [ダイナミックディスクをベーシックディスクに戻す](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc755238(v=ws.11))」を参照してください。

## <a name="syntax"></a>構文

```
convert dynamic [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

#### <a name="remarks"></a>注釈

- ベーシックディスク上の既存のパーティションは、単純ボリュームになります。

## <a name="examples"></a>例

ベーシックディスクをダイナミックディスクに変換するには、次のように入力します。

```
convert dynamic
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [convert コマンド](convert.md)
