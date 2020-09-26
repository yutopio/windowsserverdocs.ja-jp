---
title: コマンドの選択
description: 選択コマンドの参照記事。ディスク、パーティション、ボリューム、または仮想ハードディスク (VHD) にフォーカスを移動します。
ms.topic: reference
ms.assetid: 9eeb40c0-4258-46e2-8dbc-94f63497e771
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2b322fc7bf9355e64fbe14a0823c85dddadd6171
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389180"
---
# <a name="select-commands"></a>コマンドの選択

フォーカスを移動すると、ディスク、パーティション、ボリューム、またはバーチャル ハード_ディスク (VHD) します。

## <a name="syntax"></a>構文

```
select disk
select partition
select vdisk
select volume
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| [ディスクの選択](select-disk.md) | ディスクにフォーカスを移動します。 |
| [パーティションの選択](select-partition.md) | パーティションにフォーカスを移動します。 |
| [Vdisk の選択](select-vdisk.md) | VHD にフォーカスを移動します。 |
| [ボリュームの選択](select-volume.md) | ボリュームにフォーカスを移動します。 |

#### <a name="remarks"></a>解説

- 対応するパーティションを持つボリュームを選択したパーティションが自動的に選択します。

- パーティションが対応するボリュームで選択されている場合、ボリュームを自動的に選択されます。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
