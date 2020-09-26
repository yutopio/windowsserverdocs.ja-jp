---
title: set オプション
description: '[Set option] コマンドの参照記事。このオプションは、シャドウコピーの作成に関するオプションを設定します。'
ms.topic: reference
ms.assetid: 4d8d4921-9fdd-4a3c-bb0f-9df5458c4b84
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a37e993700169f0268e68822be3a7fbaf6e58361
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389058"
---
# <a name="set-option"></a>set オプション

シャドウ コピーの作成のオプションを設定します。 パラメーターを指定せずに使用する場合 **オプション設定** コマンド プロンプトでヘルプを表示します。

## <a name="syntax"></a>構文

```
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| 記号 | 指定されたボリュームの特定時点のスナップショットを作成するように指定します。 |
| p | 指定されたボリューム上のデータの特定の時点の複製コピーを作成するように指定します。 |
| 転送可能な | シャドウ コピーがまだインポートすることを示します。 メタデータの .cab ファイルは、同じまたは別のコンピューターにシャドウ コピーをインポートする後で使用できます。 |
| [rollbackrecover] | 通知を使用するライター *自動* 中に、 **PostSnapshot** イベントです。 これは、シャドウコピーがロールバックに使用される場合 (たとえば、データマイニングを使用する場合) に役立ちます。 |
| [txfrecover] | VSS の要求の作成時にトランザクション上の一貫性のシャドウ コピーを作成します。 |
| [noautorecover 回復] | 停止ライターと影に回復変更を加えるからファイル システムは、トランザクション一貫性のある状態にコピーします。 **Noautorecover 自動回復** は、 **txfrecover** または **rollbackrecover**と共に使用することはできません。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コンテキストコマンドの設定](set-context.md)

- [メタデータの設定コマンド](set-metadata.md)

- [詳細コマンドの設定](set-verbose.md)
