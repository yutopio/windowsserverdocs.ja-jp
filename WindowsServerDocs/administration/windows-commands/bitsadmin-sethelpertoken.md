---
title: bitsadmin sethelpertoken
description: Bitsadmin se pertoken コマンドの参照記事。このコマンドは、現在のコマンドプロンプトのプライマリトークン (または、指定されている場合は任意のローカルユーザーアカウントのトークン) を BITS 転送ジョブのヘルパートークンとして設定します。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 37adfc2145089a871dca819745160794ed93a68e
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028530"
---
# <a name="bitsadmin-sethelpertoken"></a>bitsadmin sethelpertoken

現在のコマンドプロンプトのプライマリトークン (または、指定されている場合は任意のローカルユーザーアカウントのトークン) を BITS 転送ジョブの [ヘルパートークン](/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)として設定します。

> [!NOTE]
> このコマンドは、BITS 3.0 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /sethelpertoken <job> [<user_name@domain> <password>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| `<username@domain>` `<password>` | 省略可能。 使用するトークンのローカルユーザーアカウントの資格情報。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
