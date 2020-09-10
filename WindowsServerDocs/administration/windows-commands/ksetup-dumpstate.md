---
title: ksetup dumpstate
description: コンピューターで定義されているすべての領域の領域設定の現在の状態を表示する、ksetup dumpstate commnand の参照記事。
ms.topic: reference
ms.assetid: 3ef2f7b8-97af-4f42-9542-cff324840637
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5f9d16a094dd3d3bbcdd5e9cb740e1bca5203a6d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639668"
---
# <a name="ksetup-dumpstate"></a>ksetup dumpstate

コンピューターに定義されているすべての領域の領域設定の現在の状態を表示します。 このコマンドは、 **ksetup** コマンドと同じ出力を表示します。

## <a name="syntax"></a>構文

```
ksetup /dumpstate
```

### <a name="remarks"></a>解説

- このコマンドの出力には、既定の領域 (コンピューターがメンバーとなっているドメイン) と、このコンピューターで定義されているすべての領域が含まれます。 各領域には次のものが含まれます。

  - この領域に関連付けられているすべてのキー配布センター (Kdc)。

  - この領域のすべての **設定領域** フラグ。

  - KDC パスワード。

- このコマンドでは、DNS の検出またはコマンドによって指定されたドメイン名は表示されません `ksetup /domain` 。

- このコマンドでは、コマンドを使用してコンピューターのパスワードを設定することはできません `ksetup /setcomputerpassword` 。

## <a name="examples"></a>例

コンピューターで Kerberos 領域構成を見つけるには、次のように入力します。

```
ksetup /dumpstate
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ksetup コマンド](ksetup.md)