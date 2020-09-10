---
title: ksetup setcomputerpassword
description: Ksetup setcomputerpassword コマンドの参照記事。ローカルコンピューターのパスワードを設定します。
ms.topic: reference
ms.assetid: e307d8f6-3b93-4c24-ac04-f31549f7dc7d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9bd9d9fafae57c1c7804f7a214d9729cdb232b2d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627438"
---
# <a name="ksetup-setcomputerpassword"></a>ksetup setcomputerpassword

ローカルコンピューターのパスワードを設定します。 このコマンドはコンピューターアカウントのみに影響し、パスワードの変更を有効にするには再起動が必要です。

> [!IMPORTANT]
> コンピューターアカウントのパスワードは、レジストリまたは **ksetup** コマンドからの出力として表示されません。

## <a name="syntax"></a>構文

```
ksetup /setcomputerpassword <password>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<password>` | ローカルコンピューターでコンピューターアカウントを設定するために、指定されたパスワードを指定します。 パスワードは、管理者特権を持つアカウントを使用してのみ設定できます。パスワードは、1 ~ 156 の英数字または特殊文字にする必要があります。 |

### <a name="examples"></a>例

ローカルコンピューターのコンピューターアカウントのパスワードを *IPops897* から *ipop $ 897!* に変更するには、次のように入力します。

```
ksetup /setcomputerpassword IPop$897!
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)
