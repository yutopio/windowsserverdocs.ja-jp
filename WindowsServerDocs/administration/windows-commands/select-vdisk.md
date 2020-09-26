---
title: select vdisk
description: Select vdisk コマンドの参照記事。指定された仮想ハードディスク (VHD) を選択し、それにフォーカスを移動します。
ms.topic: reference
ms.assetid: 8808872a-3523-4205-a6c6-83fa738ee37a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 19e842115f914711cc59cfb770ee19f732b3a388
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389208"
---
# <a name="select-vdisk"></a>select vdisk

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定した仮想ハード_ディスクを選択する \(VHD\) してフォーカスを移動します。

## <a name="syntax"></a>構文

```
select vdisk file=<full path> [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| ファイル =`<full path>` | 既存の VHD ファイルの完全パスとファイル名を指定します。 |
| noerr | スクリプト作成にのみ使用されます。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>例

*C:\test\test.vhd*という名前の VHD にフォーカスを移動するには、次のように入力します。

```
select vdisk file=c:\test\test.vhd
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [vdisk のアタッチ](attach-vdisk.md)

- [compact vdisk](compact-vdisk.md)

- [detach vdisk](detach-vdisk.md)

- [detail vdisk](detail-vdisk.md)

- [expand vdisk](expand-vdisk.md)

- [merge vdisk](merge-vdisk.md)

- [list](list.md)

- [ディスクの選択コマンド](select-disk.md)

- [パーティションの選択コマンド](select-partition.md)

- [ボリュームの選択コマンド](select-volume.md)