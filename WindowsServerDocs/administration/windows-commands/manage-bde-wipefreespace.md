---
title: manage-bde wipefreespace 領域
description: Manage-bde wipefreespace 領域の参照記事。このコマンドは、領域内に存在していた可能性のあるデータフラグメントを削除して、ボリューム上の空き領域を消去します。
ms.topic: reference
ms.assetid: b8d83a2a-c5c8-4019-9041-23d1d6abf282
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ed8d67f223cd2946dca00d556797acad31685b8e
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89635213"
---
# <a name="manage-bde-wipefreespace"></a>manage-bde wipefreespace 領域

ボリュームの空き領域を消去し、その領域内に存在していた可能性のあるデータフラグメントを削除します。 **使用領域のみ**の暗号化方法を使用して暗号化されたボリュームでこのコマンドを実行すると、**完全なボリューム暗号化**の暗号化方法と同じレベルの保護が提供されます。

## <a name="syntax"></a>構文

```
manage-bde -wipefreespace|-w [<drive>] [-cancel] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<drive>` | コロンの後にドライブ文字を表します。 |
| -キャンセル | プロセスでは、空き領域のクリーン インストールをキャンセルします。 |
| -computername | manage-bde.exe が別のコンピューターの BitLocker 保護を変更するために使用されることを指定します。 また、このコマンドの省略版として **-cn** を使用することもできます。 |
| `<name>` | BitLocker による保護を変更するコンピューターの名前を表します。 指定できる値には、コンピューターの NetBIOS 名とコンピューターの IP アドレスが含まれます。 |
| -? または /? | コマンドプロンプトで簡単なヘルプを表示します。 |
| -help または-h | 表示は、コマンド プロンプトでヘルプを完了します。 |

### <a name="examples"></a>例

ドライブ C の空き領域をワイプするには、「\」と入力します。

```
manage-bde -w C:
```

```
manage-bde -wipefreespace C:
```

C ドライブの空き領域のワイプをキャンセルするには、次のように入力します。

```
manage-bde -w -cancel C:
```

```
manage-bde -wipefreespace -cancel C:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [manage-bde コマンド](manage-bde.md)
