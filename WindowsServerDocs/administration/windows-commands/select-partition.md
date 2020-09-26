---
title: select partition
description: Select partition コマンドの参照記事。指定されたパーティションを選択し、それにフォーカスを移動します。
ms.topic: reference
ms.assetid: 25f70083-b8f7-4a8e-9b34-4b3ffbe06670
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6418ff1a08bdc12355d2b2dc75bbb7151539ae02
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389235"
---
# <a name="select-partition"></a>select partition

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定したパーティションを選択し、それに、フォーカスを移動します。 このコマンドは、現在フォーカスが、選択したディスクのパーティションを表示することもできます。

## <a name="syntax"></a>構文

```
select partition=<n>
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| partition =`<n>` | フォーカスを受け取るパーティションの数。 使用して現在選択されているディスク上のすべてのパーティションの番号を表示する、 **パーティションを一覧表示** diskpart コマンドです。 |

#### <a name="remarks"></a>解説

- 使用して、ディスクを選択するパーティションを選択する前にまず必要があります、 **select ディスク** コマンドです。

  - パーティション番号が指定されていない場合、このオプションを選択すると、選択したディスクに現在フォーカスがあるパーティションが表示されます。

  - ボリュームに対応するパーティションが選択されている場合は、パーティションが自動的に選択されます。

  - 対応するボリュームを持つパーティションが選択されている場合は、ボリュームが自動的に選択されます。

## <a name="examples"></a>例

フォーカスを *パーティション 3*に移動するには、次のように入力します。

```
select partitition=3
```

現在フォーカスが、選択したディスクのパーティションを表示するには、次のように入力します。

```
select partition
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [create partition efi コマンド](create-partition-efi.md)

- [create partition extended コマンド](create-partition-extended.md)

- [create partition logical コマンド](create-partition-logical.md)

- [パーティション msr の作成コマンド](create-partition-msr.md)

- [create partition primary コマンド](create-partition-primary.md)

- [パーティションの削除コマンド](delete-partition.md)

- [詳細パーティションコマンド](detail-partition.md)

- [ディスクの選択コマンド](select-disk.md)

- [vdisk コマンドを選択する](select-vdisk.md)

- [ボリュームの選択コマンド](select-volume.md)
