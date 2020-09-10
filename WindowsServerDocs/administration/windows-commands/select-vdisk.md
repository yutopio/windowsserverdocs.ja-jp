---
title: select vdisk
description: 参照記事 * * * *-
ms.topic: reference
ms.assetid: 8808872a-3523-4205-a6c6-83fa738ee37a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: daa6d3047e28fb8f6084824fdf1557423daa52b8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639144"
---
# <a name="select-vdisk"></a>select vdisk

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定された仮想ハードディスク VHD を選択 \( \) し、それにフォーカスを移動します。

> [!NOTE]
> このコマンドは、Windows 7 と Windows Server 2008 R2 に該当するだけです。

## <a name="syntax"></a>構文

```
select vdisk file=<full path> [noerr]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|-------|--------|
|拡張子\=<full path>|既存の VHD ファイルの完全パスとファイル名を指定します。|
|noerr|スクリプト作成にのみ使用されます。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。|

## <a name="examples"></a>例
フォーカスを Test.vhd という名前の VHD に、次のように入力します。

```
select vdisk file=c:\test\test.vhd
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

-   [vdisk のアタッチ](attach-vdisk.md)

-   [compact vdisk](compact-vdisk.md)



-   [Vdisk のデタッチ](detach-vdisk.md)

-   [detail vdisk](detail-vdisk.md)

-   [expand vdisk](expand-vdisk.md)

-   [マージ vdisk](merge-vdisk.md)

-   [list_1](./list.md)