---
title: timeout
description: タイムアウトコマンドの参照記事。指定された秒数のコマンドプロセッサを一時停止します。
ms.topic: reference
ms.assetid: e26b4a84-0e30-46e1-aa10-0667b7d3cb4c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: edb4d14614099b0e501df175e619285928344c78
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156718"
---
# <a name="timeout"></a>timeout

指定した秒数のコマンド プロセッサを一時停止します。 このコマンドは通常、バッチ ファイルで使用されます。

## <a name="syntax"></a>構文

```
timeout /t <timeoutinseconds> [/nobreak]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /t `<timeoutinseconds>` | コマンド プロセッサが処理を続行する前に待機するには、10 進数 (-1 ~ 99999) 秒数を指定します。 値 **-1** を指定すると、コンピューターはキーストロークを無期限に待機します。 |
| /nobreak | ユーザー キー ストロークを無視するように指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- ユーザーのキー入力は、タイムアウト期間の有効期限が切れていない場合でも、すぐに、コマンド プロセッサの実行を再開します。

- リソースキットの **スリープ** ツールと組み合わせて使用する場合、 **タイムアウト** は **pause** コマンドに似ています。

## <a name="examples"></a>使用例

コマンド プロセッサを一時停止、10 秒間に、次のように入力します。

```
timeout /t 10
```

100 秒のコマンド プロセッサを一時停止し、キー ストロークを無視する、次のように入力します。

```
timeout /t 100 /nobreak
```

コマンド プロセッサを一時停止、キーが押されるまで、次のように入力します。

```
timeout /t -1
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
