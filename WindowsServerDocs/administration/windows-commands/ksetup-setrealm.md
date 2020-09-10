---
title: ksetup setrealm
description: Ksetup setrealm コマンドの参照記事。 Kerberos 領域の名前を設定します。
ms.topic: reference
ms.assetid: ab268c40-276b-46ef-ab16-d5ce7667fbed
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a06c5fef1127236319b580fbd6810269c58d1377
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627133"
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
