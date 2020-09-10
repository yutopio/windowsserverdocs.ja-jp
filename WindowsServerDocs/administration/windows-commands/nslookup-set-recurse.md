---
title: nslookup set recurse
description: Nslookup set 再帰コマンドのリファレンス記事。指定されたサーバーで情報が見つからない場合に、他のサーバーを照会するようにドメインネームシステム (DNS) ネームサーバーに指示します。
ms.topic: reference
ms.assetid: d1b7a93f-dfb0-4ccd-b230-e0953057fada
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c33767e400e7bfcda0792af23673889f0afd7de9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639412"
---
# <a name="nslookup-set-recurse"></a>nslookup set recurse

指定されたサーバー上の情報が見つからない場合に、他のサーバーを照会するようにドメインネームシステム (DNS) ネームサーバーに指示します。

## <a name="syntax"></a>構文

```
set [no]recurse
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---------- | ---------- |
| norecurse | 指定されたサーバーで情報が見つからない場合に、ドメインネームシステム (DNS) ネームサーバーで他のサーバーのクエリを実行しないようにします。 |
| recurse | 指定されたサーバー上の情報が見つからない場合に、他のサーバーを照会するようにドメインネームシステム (DNS) ネームサーバーに指示します。 これが既定値です。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
