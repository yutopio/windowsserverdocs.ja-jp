---
title: expand vdisk
description: Expand vdisk コマンドの参照記事。仮想ハードディスク (VHD) を指定されたサイズに拡張します。
ms.topic: reference
ms.assetid: 3ae547b4-3813-4b86-bacd-bc273c028a2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d88570c3d8f68374f90d14a6be082f9e40bb4f6b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036400"
---
# <a name="expand-vdisk"></a>expand vdisk

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

仮想ハードディスク (VHD) を指定されたサイズに拡張します。

この操作を成功させるには、VHD を選択してデタッチする必要があります。 [Select vdisk コマンド](select-vdisk.md)を使用してボリュームを選択し、それにフォーカスを移動します。

## <a name="syntax"></a>構文

```
expand vdisk maximum=<n>
```

### <a name="parameters"></a>パラメーター

 | パラメーター | 説明 |
 |---------- | ----------- |
 | 最大 =`<n>` | VHD の新しいサイズをメガバイト (MB) 単位で指定します。 |

### <a name="examples"></a>例

選択した VHD を 20 GB まで拡張するには、次のように入力します。

```
expand vdisk maximum=20000
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [vdisk コマンドを選択する](select-vdisk.md)

- [vdisk コマンドのアタッチ](attach-vdisk.md)

- [compact vdisk コマンド](compact-vdisk.md)

- [detach vdisk コマンド](detach-vdisk.md)

- [detail vdisk コマンド](detail-vdisk.md)

- [merge vdisk コマンド](merge-vdisk.md)

- [list コマンド](list.md)
