---
title: manage-bde 変更キーを管理します。
description: オペレーティングシステムドライブのスタートアップキーを変更する manage-bde 変更キーコマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 69463db9-7e03-47ff-b233-a95d5055725f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3752d0a3a990488129b99a5ebbe44e830552c00f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622745"
---
# <a name="manage-bde-changekey"></a>manage-bde 変更キーを管理します。

オペレーティング システム ドライブのスタートアップ キーを変更します。

## <a name="syntax"></a>構文

```
manage-bde -changekey [<drive>] [<pathtoexternalkeydirectory>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| `<drive>` | コロンの後にドライブ文字を表します。 |
| -computername | manage-bde.exe が別のコンピューターの BitLocker 保護を変更するために使用されることを指定します。 また、このコマンドの省略版として **-cn** を使用することもできます。 |
| `<name>` | BitLocker による保護を変更するコンピューターの名前を表します。 指定できる値には、コンピューターの NetBIOS 名とコンピューターの IP アドレスが含まれます。 |
| -? または /? | コマンドプロンプトで簡単なヘルプを表示します。 |
| -help または-h | 表示は、コマンド プロンプトでヘルプを完了します。 |

### <a name="examples"></a>例

ドライブ E に新しいスタートアップキーを作成するには、ドライブ C で BitLocker 暗号化を使用するには、次のように入力します。

```
manage-bde -changekey C: E:\
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [manage-bde コマンド](manage-bde.md)
