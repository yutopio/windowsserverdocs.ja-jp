---
title: nslookup root
description: Nslookup root コマンドの参照記事。これにより、既定のサーバーは、ドメインネームシステム (DNS) のドメイン名空間のルートのサーバーに変更されます。
ms.topic: reference
ms.assetid: 9c29edc3-ec49-43f2-bc49-86bf0612d816
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ef505427e92b6f0e14adf92d9eea463feb582314
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038793"
---
# <a name="nslookup-root"></a>nslookup root

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ドメインネームシステム (DNS) のドメイン名空間のルートに対して、既定のサーバーをサーバーに変更します。 現時点では、ns.nic.ddn.mil ネームサーバーが使用されています。 [Nslookup set root](nslookup-set-root.md)コマンドを使用して、ルートサーバーの名前を変更できます。

> [!NOTE]
> このコマンドはと同じ `lserver ns.nic.ddn.mil` です。

## <a name="syntax"></a>構文

```
root
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [nslookup set root](nslookup-set-root.md)
