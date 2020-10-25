---
title: ライター
description: ライターコマンドの参照記事。ライターまたはコンポーネントが含まれていること、またはバックアップまたは復元の手順からライターまたはコンポーネントが含まれていることを確認します。
ms.topic: reference
ms.assetid: 7cf98295-411d-4705-8573-f898ff45c140
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d6af778ca49f8be88a08e04ecfe4165752cc796d
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524867"
---
# <a name="writer"></a>ライター

ライターまたはコンポーネントが含まれていること、または backup または restore プロシージャからライターまたはコンポーネントが除外されていることを確認します。 パラメーターを指定せずに使用した場合、 **ライター** はコマンドプロンプトでヘルプを表示します。

## <a name="syntax"></a>構文

```
writer verify [writer> | <component>]
writer exclude [<writer> | <component>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| 確認 | 指定されたライターまたはコンポーネントが、バックアップまたは復元の手順に含まれていることを確認します。 ライターまたはコンポーネントが含まれていない場合、バックアップまたは復元の手順は失敗します。 |
| 除外 | 指定されたライターまたはコンポーネントをバックアップまたは復元の手順から除外します。 |

## <a name="examples"></a>例

GUID (この例では 4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f) を指定してライターを確認するには、次のように入力します。

```
writer verify {4dc3bdd4-ab48-4d07-adb0-3bee2926fd7f}
```

*システムライター*という名前のライターを除外するには、次のように入力します。

```
writer exclude System Writer
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
