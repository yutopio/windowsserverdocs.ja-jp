---
title: auditpol remove
description: Auditpol remove コマンドの参照記事。指定されたアカウントまたはすべてのアカウントのユーザーごとの監査ポリシーを削除します。
ms.topic: reference
ms.assetid: be42ec55-235c-44f7-9abd-ed1cf3f5b1f5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a86d5e76daa7023b73760347fb5656fa13ca6418
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633173"
---
# <a name="auditpol-remove"></a>auditpol remove

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定されたアカウントまたはすべてのアカウントについて、ユーザーごとの監査ポリシーを削除します。

*ユーザーごと*のポリシーに対して*削除*操作を実行するには、セキュリティ記述子でそのオブジェクトセットの**書き込み**または**フルコントロール**のアクセス許可を持っている必要があります。 "**監査とセキュリティログの管理**" (SeSecurityPrivilege) ユーザー権利を持っている場合は、*削除*操作を実行することもできます。 ただし、この権限では、 *削除* 操作全体を実行するために必要な追加のアクセス権が許可されます。

## <a name="syntax"></a>構文

```
auditpol /remove [/user[:<username>|<{SID}>]]
[/allusers]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| /user | ユーザーごとの監査ポリシーを削除するユーザーのセキュリティ識別子 (SID) またはユーザー名を指定します。 |
| /allusers | すべてのユーザーのユーザーごとの監査ポリシーを削除します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

ユーザーごとのユーザーごとの監査ポリシーを名前で削除するには、次のように入力します。

```
auditpol /remove /user:mikedan
```

SID を使用して、ユーザーごとのユーザーごとの監査ポリシーを削除するには、次のように入力します。

```
auditpol /remove /user:{S-1-5-21-397123471-12346959}
```

すべてのユーザーのユーザーごとの監査ポリシーを削除するには、次のように入力します。

```
auditpol /remove /allusers
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [auditpol コマンド](auditpol.md)
