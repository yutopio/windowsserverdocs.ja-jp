---
title: 回復 (DiskPart)
description: DiskPart の回復コマンドの参照記事。ディスクグループ内のすべてのディスクの状態を更新し、無効なディスクグループのディスクを回復し、ミラーボリュームと古いデータを含む RAID-5 ボリュームを再同期します。
ms.topic: reference
ms.assetid: 8cc3a73d-9456-41a0-b375-2b4cc37c3992
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 55b31333f03ec90ba9c37b7d2e31c251893b18d8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637264"
---
# <a name="recover-diskpart"></a>回復 (DiskPart)

ディスクグループ内のすべてのディスクの状態を更新し、無効なディスクグループのディスクを回復します。また、古いデータを保持しているミラーボリュームと RAID-5 ボリュームを再同期します。 このコマンドは、失敗したディスクまたは失敗した場合に動作します。 また、または冗長の失敗の状態が失敗すると、失敗しているボリューム上でも機能します。

このコマンドは、ダイナミックディスクのグループに対して動作します。 ベーシックディスクを使用しているグループでこのコマンドを使用すると、エラーは返されませんが、アクションは実行されません。

> [!NOTE]
> この操作を成功させるには、ディスクグループの一部であるディスクを選択する必要があります。 [[ディスクの選択] コマンド](select-disk.md)を使用してディスクを選択し、それにフォーカスを移動します。

## <a name="syntax"></a>構文

```
recover [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>例

フォーカスのあるディスクが含まれるディスク グループを回復するには、次のように入力します。

```
recover
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
