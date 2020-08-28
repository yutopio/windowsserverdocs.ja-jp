---
title: select
description: 参照記事 * * * *-
ms.topic: reference
ms.assetid: 9eeb40c0-4258-46e2-8dbc-94f63497e771
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 6fb6230c24f723e20b09449967b157dd86347202
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032224"
---
# <a name="select"></a>select



フォーカスを移動すると、ディスク、パーティション、ボリューム、またはバーチャル ハード_ディスク (VHD) します。

## <a name="syntax"></a>構文

```
select disk
select partition
select volume
select vdisk
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|[ディスクの選択](select-disk.md)|ディスクにフォーカスを移動します。|
|[パーティションの選択](select-partition.md)|パーティションにフォーカスを移動します。|
|[ボリュームの選択](select-volume.md)|ボリュームにフォーカスを移動します。|
|[Vdisk の選択](select-vdisk.md)|VHD にフォーカスを移動します。|

## <a name="remarks"></a>解説

-   対応するパーティションを持つボリュームを選択したパーティションが自動的に選択します。
-   パーティションが対応するボリュームで選択されている場合、ボリュームを自動的に選択されます。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

