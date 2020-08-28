---
title: lpq
description: Lpq コマンドの参照記事。ラインプリンターデーモン (LPD) を実行しているコンピューターの印刷キューの状態を表示します。
ms.topic: reference
ms.assetid: bb6abcc4-310a-4fa4-927b-4084b62ca02e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: d495923b94884f0d4538839fcd3c1193e73ee938
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023706"
---
# <a name="lpq"></a>lpq

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ラインプリンターデーモン (LPD) を実行しているコンピューター上の印刷キューの状態を表示します。

## <a name="syntax"></a>構文

```
lpq -S <servername> -P <printername> [-l]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| -S `<servername>` | (名前または IP アドレスを使用して) LPD 印刷キューをホストするコンピューターまたはプリンターの共有デバイスが、表示する状態であることを指定します。 このパラメーターは必須であり、大文字にする必要があります。 |
| -P `<Printername>` | 表示するステータスを持つ印刷キューのプリンタを (名前で) 指定します。 このパラメーターは必須であり、大文字にする必要があります。 |
| -l | 印刷キューの状態に関する詳細を表示するように指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="examples"></a>例

*10.0.0.45*にある LPD ホストの*Laserprinter1*プリンターキューの状態を表示するには、次のように入力します。

```
lpq -S 10.0.0.45 -P Laserprinter1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [印刷コマンドのリファレンス](print-command-reference.md)
