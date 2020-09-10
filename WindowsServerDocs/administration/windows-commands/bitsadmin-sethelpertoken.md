---
title: bitsadmin sethelpertoken
description: Bitsadmin se pertoken コマンドの参照記事。このコマンドは、現在のコマンドプロンプトのプライマリトークン (または、指定されている場合は任意のローカルユーザーアカウントのトークン) を BITS 転送ジョブのヘルパートークンとして設定します。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: a691d010aa112f1ac609077be6a6968f79d73c72
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630914"
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
