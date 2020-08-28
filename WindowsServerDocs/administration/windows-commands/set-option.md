---
title: SET オプション
description: シャドウコピーの作成のオプションを設定する Set オプションのリファレンス記事です。
ms.topic: reference
ms.assetid: 4d8d4921-9fdd-4a3c-bb0f-9df5458c4b84
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 0569e93ee5c732369b9bc07e4452d27558412b81
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036510"
---
# <a name="set-option"></a>SET オプション

シャドウ コピーの作成のオプションを設定します。 パラメーターを指定せずに使用する場合 **オプション設定** コマンド プロンプトでヘルプを表示します。

## <a name="syntax"></a>構文

```
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
```

### <a name="parameters"></a>パラメーター

|     パラメーター     |                                                                                                  説明                                                                                                  |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|   [差分   |                                                                                                     p                                                                                                     |
|  転送可能な  |                       シャドウ コピーがまだインポートすることを示します。 メタデータの .cab ファイルは、同じまたは別のコンピューターにシャドウ コピーをインポートする後で使用できます。                       |
| [rollbackrecover] |                     通知を使用するライター *自動* 中に、 **PostSnapshot** イベントです。 これは、シャドウコピーがロールバックに使用される場合 (たとえば、データマイニングを使用する場合) に役立ちます。                      |
|   [txfrecover]    |                                                               VSS の要求の作成時にトランザクション上の一貫性のシャドウ コピーを作成します。                                                                |
|  [noautorecover 回復]  | 停止ライターと影に回復変更を加えるからファイル システムは、トランザクション一貫性のある状態にコピーします。 **Noautorecover** では使用できません **txfrecover** または **rollbackrecover**します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)