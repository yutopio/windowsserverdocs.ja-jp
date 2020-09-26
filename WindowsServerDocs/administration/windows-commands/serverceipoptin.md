---
title: serverceipoptin
description: カスタマーエクスペリエンス向上プログラム (CEIP) に参加できる serverceipoptin のリファレンス記事です。
ms.topic: reference
ms.assetid: 3d7d7fa7-0689-4797-b802-36fe260d21a0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6df387158a9630ab767dda655346836355fae936
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389170"
---
# <a name="serverceipoptin"></a>serverceipoptin

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

カスタマー エクスペリエンス向上プログラム (CEIP) に参加できます。

## <a name="syntax"></a>構文

```
serverceipoptin [/query] [/enable] [/disable]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /query | 現在の設定を確認します。 |
| /enable | CEIP への参加をオンにします。 |
| /disable | CEIP への参加をオフにします。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

現在の設定を確認するには、次のように入力します。

```
serverceipoptin /query
```

参加を有効にするには、次のように入力します。

```
serverceipoptin /enable
```

参加を無効にするには、次のように入力します。

```
serverceipoptin /disable
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
