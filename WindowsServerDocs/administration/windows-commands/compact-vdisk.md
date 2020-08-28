---
title: compact vdisk
description: Compact vdisk コマンドの参照記事。容量可変の拡張バーチャルハードディスク (VHD) ファイルの物理サイズが削減されます。
ms.topic: reference
ms.assetid: 40ca0820-67de-4160-b62a-e9bf63fe2790
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 505d04cea68a3b005490a264c8c9e77f60e22a35
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027750"
---
# <a name="compact-vdisk"></a>compact vdisk

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

容量可変の拡張バーチャルハードディスク (VHD) ファイルの物理サイズを小さくします。 このパラメーターは、ファイルを追加したときに Vhd のサイズが大きく増加するため便利ですが、ファイルを削除すると自動的にサイズが縮小されることはありません。

## <a name="syntax"></a>構文

```
compact vdisk
```

### <a name="remarks"></a>解説

- この操作を成功させるには、動的に拡張された VHD を選択する必要があります。 [Select vdisk コマンド](select-vdisk.md)を使用して VHD を選択し、それにフォーカスを移動します。

- 圧縮解除された、または読み取り専用としてアタッチされている、動的に拡張された Vhd のみを使用できます。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [vdisk コマンドのアタッチ](attach-vdisk.md)

- [detail vdisk コマンド](detail-vdisk.md)

- [Detach vdisk コマンド](detach-vdisk.md)

- [vdisk コマンドを展開する](expand-vdisk.md)

- [Merge vdisk コマンド](merge-vdisk.md)

- [vdisk コマンドを選択する](select-vdisk.md)

- [list コマンド](list.md)
