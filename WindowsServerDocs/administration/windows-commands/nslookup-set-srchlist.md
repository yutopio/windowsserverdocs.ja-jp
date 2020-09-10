---
title: nslookup set srchlist
description: Nslookup set srchlist コマンドの参照記事。既定のドメインネームシステム (DNS) のドメイン名と検索リストが変更されます。
ms.topic: reference
ms.assetid: 8486266d-22ac-4ce5-aad6-1cd0c08110a2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0d2798cd97b561ec5da7e515587978a4b19403c0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640534"
---
# <a name="nslookup-set-srchlist"></a>nslookup set srchlist

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

既定のドメインネームシステム (DNS) のドメイン名と検索一覧を変更します。 このコマンドは、 [nslookup set domain](nslookup-set-domain.md) コマンドの既定の DNS ドメイン名と検索リストを上書きします。

## <a name="syntax"></a>構文

```
set srchlist=<domainname>[/...]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<domainname>` | 既定の DNS ドメインと検索リストの新しい名前を指定します。 既定のドメイン名の値は、ホスト名に基づいています。 最大6つの名前をスラッシュ (/) で区切って指定できます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- [Nslookup set all](nslookup-set-all.md)コマンドを使用して一覧を表示します。

### <a name="examples"></a>例

DNS ドメインを *mfg.widgets.com* に設定し、検索リストを3つの名前に設定するには、次のようにします。

```
set srchlist=mfg.widgets.com/mrp2.widgets.com/widgets.com
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [nslookup set domain](nslookup-set-domain.md)

- [nslookup set all](nslookup-set-all.md)
