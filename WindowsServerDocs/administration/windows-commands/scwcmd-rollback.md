---
title: Scwcmd ロールバック
description: 参照記事 * * * *-
ms.topic: reference
ms.assetid: 4fd9f89b-0420-420a-ad20-4a328636b1e7
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 25c726b649028f66ca97ebc0280175d1713b7ef7
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036180"
---
# <a name="scwcmd-rollback"></a>Scwcmd: ロールバック

> 適用対象: Windows Server 2012 R2、Windows Server 2012

使用可能な最新のロールバックのポリシーを適用し、そのロールバックのポリシーを削除します。

## <a name="syntax"></a>構文

```
scwcmd rollback /m:<ComputerName> [/u:<UserName>] [/pw:<Password>]
```

#### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|/m\<ComputerName>|NetBIOS 名、DNS 名、またはロールバック操作が実行するコンピューターの IP アドレスを指定します。|
|/u\<UserName>|リモートのロールバックを実行するときに使用する代替のユーザー アカウントを指定します。 既定値は、ユーザーには、ログオンしています。|
|pw\<Password>|リモートのロールバックを実行するときに使用する、代替のユーザー資格情報を指定します。 既定値は、ユーザーには、ログオンしています。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>解説

Scwcmd.exe は Windows Server 2008 R2、Windows Server 2008 または Windows Server 2003 を実行するコンピューターにできるだけです。

## <a name="examples"></a>例

「172.16.0.0」の IP アドレスにあるコンピューターで、セキュリティ ポリシーをロールバックするには、次ように入力します。
```
scwcmd rollback /m:172.16.0.0
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)