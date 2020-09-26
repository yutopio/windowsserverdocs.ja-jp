---
title: scwcmd rollback
description: Scwcmd rollback コマンドの参照記事。利用可能な最新のロールバックポリシーが適用され、そのロールバックポリシーが削除されます。
ms.topic: reference
ms.assetid: 4fd9f89b-0420-420a-ad20-4a328636b1e7
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e8f50995131ca01ea2bb58ee9371b12d9ec9a917
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388912"
---
# <a name="scwcmd-rollback"></a>scwcmd rollback

> 適用対象: Windows Server 2012 R2 および Windows Server 2012

使用可能な最新のロールバックのポリシーを適用し、そのロールバックのポリシーを削除します。

## <a name="syntax"></a>構文

```
scwcmd rollback /m:<computername> [/u:<username>] [/pw:<password>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /m`<computername>` | NetBIOS 名、DNS 名、またはロールバック操作が実行するコンピューターの IP アドレスを指定します。 |
| /u`<username>` | リモートのロールバックを実行するときに使用する代替のユーザー アカウントを指定します。 既定値は、ユーザーには、ログオンしています。 |
| pw`<password>` | リモートのロールバックを実行するときに使用する、代替のユーザー資格情報を指定します。 既定値は、ユーザーには、ログオンしています。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

IP アドレス *172.16.0.0*でコンピューターのセキュリティポリシーをロールバックするには、次のように入力します。

```
scwcmd rollback /m:172.16.0.0
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [scwcmd analyze コマンド](scwcmd-analyze.md)

- [scwcmd configure コマンド](scwcmd-configure.md)

- [scwcmd register コマンド](scwcmd-register.md)

- [scwcmd transform コマンド](scwcmd-transform.md)

- [scwcmd view コマンド](scwcmd-view.md)