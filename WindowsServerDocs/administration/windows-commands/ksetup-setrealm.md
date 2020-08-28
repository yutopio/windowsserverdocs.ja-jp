---
title: ksetup setrealm
description: Ksetup setrealm コマンドの参照記事。 Kerberos 領域の名前を設定します。
ms.topic: reference
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 53de8c94e20f496a6f3078d3ad03a817f23e326a
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025366"
---
# <a name="ksetup-setrealm"></a>ksetup setrealm

Kerberos 領域の名前を設定します。

> [!IMPORTANT]
> ドメインコントローラーでの Kerberos 領域の設定はサポートされていません。 これを行おうとすると、警告とコマンドエラーが発生します。

## <a name="syntax"></a>構文

```
ksetup /setrealm <DNSdomainname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<DNSdomainname>` | CORP など、大文字の DNS 名を指定します。CONTOSO.COM。 完全修飾ドメイン名を使用することも、名前の単純な形式を使用することもできます。 DNS 名に大文字を使用しない場合は、続行するかどうかを確認するメッセージが表示されます。 |

### <a name="examples"></a>例

このコンピューターの領域を特定のドメイン名に設定し、ドメインコントローラー以外のアクセスを CONTOSO Kerberos 領域のみに制限するには、次のように入力します。

```
ksetup /setrealm CONTOSO
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)

- [ksetup removerealm](ksetup-removerealm.md)
