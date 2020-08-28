---
title: nslookup set search
description: Nslookup set search コマンドのリファレンス記事。応答が受信されるまで、DNS ドメインの検索リストにドメインネームシステム (DNS) のドメイン名を追加します。
ms.topic: reference
ms.assetid: 064ac660-8b04-4af9-8b2c-e4e0549771b8
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 17cee7cbc2112db346c91ab4a7b88264eff6a850
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025156"
---
# <a name="nslookup-set-search"></a>nslookup set search

DNS ドメイン検索リスト内のドメインネームシステム (DNS) ドメイン名を、応答が受信されるまで要求に追加します。 これは、セットと参照要求に少なくとも1つのピリオドが含まれている場合に適用されますが、末尾にピリオドは付きません。

## <a name="syntax"></a>構文

```
set [no]search
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| nosearch | 要求の DNS ドメイン検索一覧にドメインネームシステム (DNS) ドメイン名の追加を停止します。 |
| 検索 | 応答が受信されるまで、要求の DNS ドメイン検索一覧にドメインネームシステム (DNS) のドメイン名を追加します。 これが既定値です。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
