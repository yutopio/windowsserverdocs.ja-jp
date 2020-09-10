---
title: ksetup delhosttorealmmap
description: 指定されたホストと領域間のサービスプリンシパル名 (SPN) マッピングを削除する ksetup delhost almmap コマンドの参照記事。
ms.topic: reference
ms.assetid: 3faee482-a96c-4614-86fd-aaa446643ec4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 321d468169005d5b183e3b3d4149872a731b8cfa
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639697"
---
# <a name="ksetup-delhosttorealmmap"></a>ksetup delhosttorealmmap

指定されたホストと領域間のサービスプリンシパル名 (SPN) マッピングを削除します。 また、このコマンドは、ホストと領域間のマッピング (または複数のホストをレルムに) を削除します。

マッピングは、レジストリのの下に格納され `HKEY_LOCAL_MACHINE\SYSTEM\CurrentContolSet\Lsa\Kerberos\HostToRealm` ます。 このコマンドを実行した後、マッピングがレジストリに表示されることを確認することをお勧めします。

## <a name="syntax"></a>構文

```
ksetup /delhosttorealmmap <hostname> <realmname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<hostname>` | コンピューターの完全修飾ドメイン名を指定します。 |
| `<realmname>` | CORP など、大文字の DNS 名を指定します。CONTOSO.COM。 |

### <a name="examples"></a>例

領域 CONTOSO の構成を変更し、ホストコンピューター IPops897 の領域へのマッピングを削除するには、次のように入力します。

```
ksetup /delhosttorealmmap IPops897 CONTOSO
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)

- [ksetup addhost almmap コマンド](ksetup-addhosttorealmmap.md)
