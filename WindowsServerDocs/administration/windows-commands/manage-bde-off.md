---
title: manage-bde をオフにします
description: ドライブの暗号化を解除し、BitLocker をオフにする manage-bde コマンドの参照記事。
ms.topic: reference
ms.assetid: 0a27c119-d385-45e5-89fe-e311d4429876
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c85fec912802c6f0bac7494c9a3192623ac55686
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037660"
---
# <a name="manage-bde-off"></a>manage-bde をオフにします

ドライブの暗号化を解除し、BitLocker をオフにします。 復号化が完了すると、すべてのキー プロテクターが削除されます。

## <a name="syntax"></a>構文

```
manage-bde -off [<volume>] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<volume>` | ドライブ文字の後にコロン、ボリューム GUID パス、またはマウントされたボリュームを指定します。 |
| -computername | manage-bde.exe が別のコンピューターの BitLocker 保護を変更するために使用されることを指定します。 また、このコマンドの省略版として **-cn** を使用することもできます。 |
| `<name>` | BitLocker による保護を変更するコンピューターの名前を表します。 指定できる値には、コンピューターの NetBIOS 名とコンピューターの IP アドレスが含まれます。 |
| -? または /? | コマンドプロンプトで簡単なヘルプを表示します。 |
| -help または-h | 表示は、コマンド プロンプトでヘルプを完了します。 |

### <a name="examples"></a>例

ドライブ C で BitLocker をオフにするには、次のように入力します。

```
manage-bde –off C:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コマンドの manage-bde を管理する](manage-bde-on.md)

- [manage-bde pause コマンド](manage-bde-pause.md)

- [manage-bde resume コマンド](manage-bde-resume.md)

- [manage-bde コマンド](manage-bde.md)
