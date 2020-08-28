---
title: reset
description: Reset コマンドの参照記事。 DiskShadow.exe を既定の状態にリセットします。
ms.topic: reference
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 9ca1b0574fae1e0d00bc1f2cbec17ff9572ed253
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038340"
---
# <a name="reset"></a>reset

DiskShadow.exe を既定の状態にリセットします。 このコマンドは、作成、**インポート**、**バックアップ**、**復元**などの複合 DiskShadow 操作を分離**する**場合に特に役立ちます。

> [!重要このコマンドを実行すると、 **追加**、 **設定**、 **読み込み**、 **ライター**などのコマンドからの状態情報が失われます。 このコマンドでは、IVssBackupComponent インターフェイスも解放され、非永続的なシャドウコピーは失われます。

## <a name="syntax"></a>構文

```
reset
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [create コマンド](create.md)

- [import コマンド](import_1.md)

- [backup コマンド](begin-backup.md)

- [restore コマンド](begin-restore.md)

- [コマンドの追加](add.md)

- [set コマンド](set_2.md)

- [load コマンド](reg-load.md)

- [writer コマンド](writer.md)
