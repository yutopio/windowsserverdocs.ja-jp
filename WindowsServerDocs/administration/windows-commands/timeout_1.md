---
title: timeout
description: タイムアウトの参照記事。指定された秒数のコマンドプロセッサを一時停止します。
ms.topic: reference
ms.assetid: e26b4a84-0e30-46e1-aa10-0667b7d3cb4c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9a4a1a0a352361e901a7344baeb2c92f36e41870
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640431"
---
# <a name="timeout"></a>timeout

指定した秒数のコマンド プロセッサを一時停止します。



## <a name="syntax"></a>構文

```
timeout /t <TimeoutInSeconds> [/nobreak]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|/t \<TimeoutInSeconds>|コマンド プロセッサが処理を続行する前に待機するには、10 進数 (-1 ~ 99999) 秒数を指定します。 値-1 は、キーストロークを無期限に待機するコンピューターです。|
|/nobreak|ユーザー キー ストロークを無視するように指定します。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>注釈

-   **タイムアウト** コマンドは、通常、バッチ ファイルで使用します。
-   ユーザーのキー入力は、タイムアウト期間の有効期限が切れていない場合でも、すぐに、コマンド プロセッサの実行を再開します。
-   組み合わせて使用すると、 **スリープ** コマンド、 **タイムアウト** に似ていますが、 **を一時停止** コマンドです。

## <a name="examples"></a>例

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

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
