---
title: ksetup domain
description: Ksetup domain コマンドの参照記事。すべての Kerberos 操作のドメイン名を設定します。
ms.topic: reference
ms.assetid: 2ef766e3-6071-44f2-946b-22ea5b61a508
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: dcb7624f7b9fa81c66fed4533a0ba377095fa902
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640050"
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