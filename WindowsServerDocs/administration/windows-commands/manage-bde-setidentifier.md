---
title: manage-bde setidentifier
description: Manage-bde setidentifier コマンドのリファレンス記事。ドライブの [ドライブ識別子] フィールドを、[組織の一意の識別子を指定してくださいグループポリシー] 設定で指定された値に設定します。
ms.topic: reference
ms.assetid: 7092d18f-4ac9-4c73-a20f-1246ca60e75e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 861eca94cb15c70857138b6f9c76b5dcf59089a9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634339"
---
# <a name="manage-bde-setidentifier"></a>manage-bde setidentifier

指定された値にドライブのドライブ識別子のフィールドを設定、 **、組織の一意の識別子を提供する** グループ ポリシー設定です。

## <a name="syntax"></a>構文

```
manage-bde –setidentifier <drive> [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<drive>` | コロンの後にドライブ文字を表します。 |
| -computername | manage-bde.exe が別のコンピューターの BitLocker 保護を変更するために使用されることを指定します。 また、このコマンドの省略版として **-cn** を使用することもできます。 |
| `<name>` | BitLocker による保護を変更するコンピューターの名前を表します。 指定できる値には、コンピューターの NetBIOS 名とコンピューターの IP アドレスが含まれます。 |
| -? または /? | コマンドプロンプトで簡単なヘルプを表示します。 |
| -help または-h | 表示は、コマンド プロンプトでヘルプを完了します。 |

### <a name="examples"></a>例

C の BitLocker ドライブ識別子フィールドを設定するには、次のように入力します。

```
manage-bde –setidentifier C:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [manage-bde コマンド](manage-bde.md)

- [BitLocker 回復ガイド](/windows/security/information-protection/bitlocker/bitlocker-recovery-guide-plan)
