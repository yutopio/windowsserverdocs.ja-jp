---
title: nslookup set root
description: Nslookup set root コマンドのリファレンス記事。クエリに使用されるルートサーバーの名前を変更します。
ms.topic: reference
ms.assetid: 8ad5393c-d4fd-4594-8187-576b1dcde60a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d7e1251b7e13320a77a4c59736a6bd985bd248af
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637479"
---
# <a name="nslookup-set-root"></a>nslookup set root

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

クエリに使用するルートサーバーの名前を変更します。

> [!NOTE]
> このコマンドでは、 [nslookup root](nslookup-root.md) コマンドがサポートされています。

## <a name="syntax"></a>構文

```
set root=<rootserver>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---------- | ---------- |
| `<rootserver>` | ルートサーバーの新しい名前を指定します。 既定値は **ns.nic.ddn.mil**です。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [nslookup root](nslookup-root.md)
