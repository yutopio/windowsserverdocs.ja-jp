---
title: ksetup domain
description: Ksetup domain コマンドの参照記事。すべての Kerberos 操作のドメイン名を設定します。
ms.topic: reference
ms.assetid: 2ef766e3-6071-44f2-946b-22ea5b61a508
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c9e89023e127318139672581cbab267a34c67a58
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89025536"
---
# <a name="ksetup-domain"></a>ksetup domain

すべての Kerberos 操作のドメイン名を設定します。

## <a name="syntax"></a>構文

```
ksetup /domain <domainname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<domainname>` | 接続を確立するドメインの名前。 完全修飾ドメイン名、または名前の単純な形式 (contoso.com や contoso など) を使用します。|

### <a name="examples"></a>例

サブコマンドを使用して、Microsoft などの有効なドメインへの接続を確立するには、次のように `ksetup /mapuser` 入力します。

```
ksetup /mapuser principal@realm domain-user /domain domain-name
```

接続に成功すると、新しい TGT が送信されるか、既存の TGT が更新されます。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)

- [ksetup mapuser コマンド](ksetup-mapuser.md)