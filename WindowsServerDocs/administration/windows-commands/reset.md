---
title: reset
description: Reset コマンドの参照記事。 DiskShadow.exe を既定の状態にリセットします。
ms.topic: reference
ms.assetid: afbdab44-199c-4e11-884f-e96804965c21
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 84f4aedee746e642e59a09055c3994160f503afa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626881"
---
# <a name="reset"></a>reset

DiskShadow.exe を既定の状態にリセットします。 このコマンドは、作成、**インポート**、**バックアップ**、**復元**などの複合 DiskShadow 操作を分離**する**場合に特に役立ちます。

> [!重要このコマンドを実行すると、 **追加**、 **設定**、 **読み込み**、 **ライター**などのコマンドからの状態情報が失われます。 このコマンドでは、IVssBackupComponent インターフェイスも解放され、非永続的なシャドウコピーは失われます。

## <a name="syntax"></a>Syntax

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
