---
title: online disk
description: オンラインディスクコマンドの参照記事。オフラインディスクがオンライン状態になります。
ms.topic: reference
ms.assetid: bc44a783-eaa4-40ca-be01-5703b5bf4eb3
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a2c33a85a8217963a220495e75efebf0c6999309
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627323"
---
# <a name="online-disk"></a>online disk

オフラインディスクをオンライン状態にします。 ベーシックディスクの場合、このコマンドは、選択したディスクとそのディスク上のすべてのボリュームをオンラインにしようとします。 ダイナミックディスクの場合、このコマンドは、ローカルコンピューター上で外部とマークされていないすべてのディスクをオンラインにしようとします。 また、ダイナミックディスクのセットにあるすべてのボリュームをオンラインにしようとします。

ディスクグループ内のダイナミックディスクがオンラインになり、グループ内の唯一のディスクである場合は、元のグループが再作成され、ディスクがそのグループに移動されます。 グループ内に他のディスクがあり、それらがオンラインになっている場合、ディスクは単にグループに戻されます。 選択したディスクのグループにミラーボリュームまたは RAID-5 ボリュームが含まれている場合は、このコマンドによってこれらのボリュームも再同期されます。

> [!NOTE]
> **オンラインディスク**コマンドを正常に実行するには、ディスクを選択する必要があります。 使用して、 [select ディスク](select-disk.md) コマンド ディスクを選択し、それにフォーカスをします。

> [!IMPORTANT]
> 読み取り専用ディスクで使用されている場合、このコマンドは失敗します。

## <a name="syntax"></a>構文

```
online disk [noerr]
```

### <a name="parameters"></a>パラメーター

このコマンドの使用方法について [は、「不足またはオフラインのダイナミックディスクを再アクティブ化する](/previous-versions/windows/it-pro/windows-server-2008-r2-and-2008/cc732026(v=ws.11))」を参照してください。

| パラメーター | Description |
|--|--|
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

### <a name="examples"></a>例

フォーカスがあるディスクをオンラインにするには、次のように入力します。

```
online disk
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
