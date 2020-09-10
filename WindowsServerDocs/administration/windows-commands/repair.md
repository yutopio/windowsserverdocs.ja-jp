---
title: 修復
description: 修復コマンドの参照記事。障害が発生したディスク領域を指定されたダイナミックディスクに交換することによって RAID-5 ボリュームを修復します。
ms.topic: reference
ms.assetid: 9f84f661-f3cd-48c8-bf08-87819cf626fe
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 969a677f72af9ab5e99770983308db6e88c28c29
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89641002"
---
# <a name="repair"></a>修復

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

障害が発生したディスク領域を指定されたダイナミックディスクに交換することで、フォーカスのある RAID-5 ボリュームを修復します。

この操作を成功させるには、RAID-5 アレイ内のボリュームを選択する必要があります。 使用して、 **ボリュームを選択して** コマンドのボリュームを選択し、それにフォーカスをします。

## <a name="syntax"></a>構文

```
repair disk=<n> [align=<n>] [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| ディスク =`<n>` | 障害が発生したディスク領域を置き換えるダイナミックディスクを指定します。 ここで、 *n* には、raid-5 ボリューム内の障害が発生したディスク領域の合計サイズ以上の空き領域が必要です。 |
| align =`<n>` | すべてのボリュームまたはパーティションエクステントを最も近いアラインメント境界に配置します。 ここで *n* は、ディスクの先頭から最も近いアラインメント境界までのキロバイト (kb) の数です。 |
| noerr | スクリプトの場合のみ。 エラーが発生した場合、DiskPart はエラーが発生しなかったかのようにコマンドを処理し続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

### <a name="examples"></a>例

ダイナミックディスク4に置き換えることによって、フォーカスのあるボリュームを置き換えるには、次のように入力します。

```
repair disk=4
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ボリュームの選択コマンド](select-volume.md)