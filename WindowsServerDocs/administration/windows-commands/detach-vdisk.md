---
title: detach vdisk
description: Detach vdisk コマンドの参照記事。選択した仮想ハードディスク (VHD) がホストコンピューター上のローカルハードディスクドライブとして表示されなくなります。
ms.topic: reference
ms.assetid: 5f01dcb8-9237-4564-ad94-8a8dd0fd0cca
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: af3608cfa3f92ecbda3c62401f5c5a85fa5a2ffe
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89628764"
---
# <a name="detach-vdisk"></a>detach vdisk

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

選択した仮想ハードディスク (VHD) がホストコンピューター上のローカルハードディスクドライブとして表示されなくなります。 VHD をデタッチすると、他の場所に VHD をコピーできます。 開始する前に、この操作を成功させる VHD を選択する必要があります。 使用して、 [vdisk を選択して](select-vdisk.md) コマンド、VHD を選択し、それにフォーカスをします。


## <a name="syntax"></a>構文

```
detach vdisk [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>例

選択した VHD をデタッチするには、次のように入力します。

```
detach vdisk
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [vdisk コマンドのアタッチ](attach-vdisk.md)

- [compact vdisk コマンド](compact-vdisk.md)

- [detail vdisk コマンド](detail-vdisk.md)

- [vdisk コマンドを展開する](expand-vdisk.md)

- [Merge vdisk コマンド](merge-vdisk.md)

- [vdisk コマンドを選択する](select-vdisk.md)

- [list コマンド](list.md)
