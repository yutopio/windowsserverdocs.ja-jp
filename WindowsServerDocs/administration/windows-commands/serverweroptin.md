---
title: serverweroptin
description: Serverweroptin コマンドの参照記事。これにより、エラー報告を有効にすることができます。
ms.topic: reference
ms.assetid: f3c0b0af-cafb-4f09-8b36-5a357ddf392d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c8a2fe32634704a22f12430b8516ed7f6cae4e82
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389134"
---
# <a name="serverweroptin"></a>serverweroptin

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

エラー報告を有効にすることができます。

## <a name="syntax"></a>構文

```
serverweroptin [/query] [/detailed] [/summary]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /query | 現在の設定を確認します。 |
| 詳細な/ | 詳細レポートを自動的に送信するように指定します。 |
| 概要/ | 概要レポートを自動的に送信するように指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

現在の設定を確認するには、次のように入力します。

```
serverweroptin /query
```

詳細レポートを自動的に送信するには、次のように入力します。

```
serverweroptin /detailed
```

自動的に概要レポートを送信するには、次のように入力します。

```
serverweroptin /summary
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
