---
title: 非アクティブ
description: 非アクティブなコマンドの参照記事。ベーシックマスターブートレコード (MBR) ディスクで、フォーカスがあるシステムパーティションまたはブートパーティションを非アクティブとしてマークします。
ms.topic: reference
ms.assetid: f4fb4695-4e66-4166-b4ab-2c86a4605580
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 265e1ca2ef7c352aead87ab19bdabed3a0abe476
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634503"
---
# <a name="inactive"></a>非アクティブ

基本マスターブートレコード (MBR) ディスクで、フォーカスがあるシステムパーティションまたはブートパーティションを非アクティブとしてマークします。

この操作を成功させるには、アクティブなシステムまたはブートパーティションを選択する必要があります。 [[パーティションの選択] コマンド](select-partition.md)を使用してアクティブなパーティションを選択し、それにフォーカスを移動します。

> [!CAUTION]
> アクティブ パーティションがないコンピューターは、起動しない可能性があります。 システムまたはブートパーティションを非アクティブとしてマークしないでください。これは、Windows ファミリのオペレーティングシステムを十分に理解している経験豊富なユーザーでない限りです。<p>システムパーティションまたはブートパーティションを非アクティブとしてマークした後にコンピューターを起動できない場合は、cd-rom ドライブに Windows セットアップ CD を挿入し、コンピューターを再起動してから、回復コンソールの **fixmbr** コマンドと **fixboot** コマンドを使用してパーティションを修復します。
>
> システムパーティションまたはブートパーティションを非アクティブとしてマークした後、コンピューターは、CD-ROM ドライブやプリブート実行環境 (PXE) など、BIOS で指定されている次のオプションから起動します。

## <a name="syntax"></a>構文

```
inactive
```

### <a name="examples"></a>例

```
inactive
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [パーティションの選択コマンド](select-partition.md)

- [Windows の起動の問題の高度なトラブルシューティング](/windows/client-management/advanced-troubleshooting-boot-problems)
