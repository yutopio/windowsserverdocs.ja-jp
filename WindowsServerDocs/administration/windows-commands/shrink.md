---
title: shrink
description: DiskPart の圧縮コマンドの参照記事。指定した量だけ、選択したボリュームのサイズが小さくなります。
ms.topic: reference
ms.assetid: ec87cc7c-9846-465e-a10d-4ee10db4f4e6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8b03c006243f263a4f1c7fe991580d5e74f9a7a7
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718319"
---
# <a name="shrink"></a>shrink

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Diskpart の [圧縮] コマンドを使用すると、指定した量だけ選択したボリュームのサイズが縮小されます。 このコマンドでは、ボリュームの最後に、未使用の領域から使用可能な空きディスク領域を作成します。

この操作を成功させるのには、ボリュームを選択してください。 使用して、 **ボリュームを選択して** コマンドのボリュームを選択し、それにフォーカスをします。

> [!NOTE]
> このコマンドは、ベーシック ボリュームとシンプル ボリュームまたはスパン ダイナミック ボリュームは機能します。 これは、相手先ブランド供給 (OEM) パーティション、拡張ファームウェアインターフェイス (EFI) システムパーティション、または回復パーティションでは機能しません。

## <a name="syntax"></a>構文

```
shrink [desired=<n>] [minimum=<n>] [nowait] [noerr]
shrink querymax [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| 必要な =`<n>` | メガバイト (MB)、ボリュームのサイズを小さく領域の必要な量を指定します。 |
| 最小 =`<n>` | (Mb) ではボリュームのサイズを小さくには、領域の最小容量を指定します。 |
| querymax | ボリュームを削減できます (mb) の領域の最大量を返します。 アプリケーションは、ボリュームを現在アクセスしている場合、この値を変更できます。 |
| nowait | 進行中の圧縮処理中にすぐに取得するコマンドがするように指定します。 |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

#### <a name="remarks"></a>解説

- NTFS ファイル システムでフォーマットされている場合またはファイル システムがあるない場合にのみ、ボリュームのサイズを小さくことができます。

- 必要な量が指定されていない場合は、ボリュームの最小量が減少します (指定されている場合)。

- 最小量が指定されていない場合は、必要な量だけボリュームが縮小されます (指定されている場合)。

- 最小量も目的の量も指定されていない場合、ボリュームはできるだけ小さくなります。

- 最小量が指定されていても、十分な空き領域がない場合、コマンドは失敗します。

## <a name="examples"></a>例

選択したボリュームのサイズを減らすためを 250 および 500 件のメガバイト数の間で最大の可能な量には、次のように入力します。

```
shrink desired=500 minimum=250
```

削減されることができます、ボリュームを mb 単位の最大数を表示するには、次のように入力します。

```
shrink querymax
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [パーティションのサイズ変更](/powershell/module/storage/resize-partition?view=win10-ps&preserve-view=true)
