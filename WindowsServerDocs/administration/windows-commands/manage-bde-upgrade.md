---
title: manage-bde のアップグレード
description: BitLocker バージョンをアップグレードする manage-bde upgrade コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 23bfa824-6ff0-44cc-9b8b-b199a769fb8d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a031c06068a8dc1b66b4065e19d85ab5b62ea7e6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635256"
---
# <a name="manage-bde-upgrade"></a>manage-bde のアップグレード

BitLocker のバージョンにアップグレードします。

## <a name="syntax"></a>構文

```
manage-bde -upgrade [<drive>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<drive>` | コロンの後にドライブ文字を表します。 |
| -computername | manage-bde.exe が別のコンピューターの BitLocker 保護を変更するために使用されることを指定します。 また、このコマンドの省略版として **-cn** を使用することもできます。 |
| `<name>` | BitLocker による保護を変更するコンピューターの名前を表します。 指定できる値には、コンピューターの NetBIOS 名とコンピューターの IP アドレスが含まれます。 |
| -? または /? | コマンドプロンプトで簡単なヘルプを表示します。 |
| -help または-h | 表示は、コマンド プロンプトでヘルプを完了します。 |

## <a name="examples"></a>例

ドライブ C の BitLocker 暗号化をアップグレードするには、次のように入力します。

```
manage-bde –upgrade C:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [manage-bde コマンド](manage-bde.md)
