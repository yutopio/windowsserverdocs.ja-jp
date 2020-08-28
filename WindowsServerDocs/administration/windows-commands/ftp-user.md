---
title: ftp user
description: リモートコンピューターに対してユーザーを指定する、ftp ユーザーコマンドの参照記事です。
ms.topic: reference
ms.assetid: 0a77bfeb-27a9-4f2f-a3c4-2fef529fb569
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7c1e928dd3aa30784d607da6f84ad9ae024881f3
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89035660"
---
# <a name="ftp-user"></a>ftp user

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモート コンピューターにユーザーを指定します。

## <a name="syntax"></a>構文

```
user <username> [<password>] [<account>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<username>` | リモート コンピューターへのログオンに使用するユーザー名を指定します。 |
| `[<password>]` | *ユーザー名*のパスワードを指定します。 パスワードが指定されておらず、必須の場合は、 **ftp** コマンドによってパスワードの入力が求められます。 |
| `[<account>]` | リモート コンピューターへのログオンに使用するアカウントを指定します。 *アカウント*が指定されておらず、必須の場合は、 **ftp**コマンドによってアカウントの入力が求められます。 |

### <a name="examples"></a>例

パスワード*Password1*を使用して*User1*を指定するには、次のように入力します。

```
user User1 Password1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
