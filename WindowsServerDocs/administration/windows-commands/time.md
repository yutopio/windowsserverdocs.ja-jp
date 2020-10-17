---
title: time
description: 時刻コマンドの参照記事。システム時刻を表示または設定します。
ms.topic: reference
ms.assetid: 1276a257-7283-41da-ae80-fb4cfb311f9d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b69db2fce1af52d8f284e79fe83f5ac20c398cd6
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156471"
---
# <a name="time"></a>time

表示またはシステム時刻を設定します。 パラメーターを指定せずに使用する場合 **時間** 現在のシステム時刻が表示され、新しい時間を入力するように求められます。

> [!NOTE]
> 現在の時刻を変更するには、管理者である必要があります。

## <a name="syntax"></a>構文

```
time [/t | [<HH>[:<MM>[:<SS>]] [am|pm]]]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<HH>[:<MM>[:<SS>[.<NN>]]] [am | pm]` | システム時刻を指定された、新しい時間に設定 *HH* (必要)、時間単位で *MM* 分単位で、 *SS* の秒数。 *NN* の秒を指定するために使用できます。 値を区切る必要があります *HH*, 、*MM*, 、および *SS* コロン (::)。 *SS* と *NN* ピリオド (.) で区切る必要があります。<p>**Am**または**pm**が指定されていない場合、**時刻**は既定で24時間形式を使用します。 |
| /t | ときに、新しいメッセージを表示せずには、現在の時刻を表示します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- 有効な *HH* 値は 0 ~ 24 です。

- 有効な *MM* と *SS* 値は 0 ~ 59 です。

## <a name="examples"></a>使用例

コマンド拡張機能が有効になっている場合は、現在のシステム時刻を表示するを入力します。

```
time /t
```

現在のシステム時刻を 5:30 PM に変更するには、次のいずれかを入力します。

```
time 17:30:00
time 5:30 pm
```

新しい時間を入力するプロンプトが後に現在のシステム時刻を表示するには、次のように入力します。

```
The current time is: 17:33:31.35
Enter the new time:
```

現在の時刻を保持し、コマンド プロンプトに戻り、ENTER キーを押します。 現在の時刻を変更するには、新しい時間を入力し、ENTER キーを押します。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
