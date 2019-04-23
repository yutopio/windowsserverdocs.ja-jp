---
title: tasklist
description: ローカルまたはリモート コンピューターで実行されているプロセスの一覧を表示する方法について説明します。
ms.custom: na
ms.prod: windows-server-threshold
ms.reviewer: na
ms.suite: na
ms.technology: manage-windows-commands
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8dbe30ee-1484-46be-917b-5ca3ff4fdc9c
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: abb36c8c794836387af5547f3706e910dc06fa42
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59843003"
---
# <a name="tasklist"></a>tasklist

ローカル コンピューターまたはリモート コンピューター上で現在実行中のプロセスの一覧を表示します。 **Tasklist** 置き換えます、 **tlist** ツールです。

このコマンドを使用する方法の例については、[例](#BKMK_examples)を参照してください。

## <a name="syntax"></a>構文

```
tasklist [/s <Computer> [/u [<Domain>\]<UserName> [/p <Password>]]] [{/m <Module> | /svc | /v}] [/fo {table | list | csv}] [/nh] [/fi <Filter> [/fi <Filter> [ ... ]]]
```

## <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|/s\<コンピューター >|名前またはリモート コンピューターの IP アドレスを指定します (円記号を使用しない)。 既定はローカル コンピュータです。|
|/u [\<ドメイン >\\\]\<ユーザー名 >|指定されているユーザーのアカウント権限でコマンドを実行*UserName*または*ドメイン*\*ユーザー名 *。 **/u** 場合にのみ指定できる **/s** を指定します。 既定では、コマンドを発行しているコンピューターに現在ログオンしているユーザーのアクセス許可です。|
|/p\<パスワード >|指定されているユーザー アカウントのパスワードを指定します、 **/u** パラメーター。|
|/m\<モジュール >|読み込まれた DLL モジュールを指定したパターンの名前に一致するすべてのタスクを一覧表示します。 モジュール名が指定されていない場合、このオプションは、各タスクによって読み込まれたすべてのモジュールを表示します。|
|/svc|切り捨てることがなく、各プロセスのすべてのサービス情報を一覧表示します。 有効な場合に、 **/fo** にパラメーターが設定されている **テーブル**します。|
|/v|出力に詳細なタスクの情報を表示します。 切り捨てることがなく完全な詳細な出力を使用して **/v** と **/svc** 化します。|
|/fo {テーブル\|一覧\|csv}|使用して、出力形式を指定します。 有効な値は **テーブル**, 、**リスト**, 、および **csv**します。 出力の既定の形式は**テーブル**します。|
|/nh|出力に列ヘッダーを抑制します。 有効な場合に、 **/fo** にパラメーターが設定されている **テーブル** または **csv**します。|
|/fi\<フィルター >|含めることも、クエリから除外するプロセスの種類を指定します。 有効なフィルター名、演算子、および値については、次の表を参照してください。|
|/?|コマンド プロンプトにヘルプを表示します。|

### <a name="filter-names-operators-and-values"></a>フィルター名、演算子、および値

|フィルター名|有効な演算子|有効な値|
|-----------|---------------|------------|
|状態|eq、ne|RUNNING | 応答していません。 | 不明|
|IMAGENAME|eq、ne|イメージの名前|
|PID|eq、ne、gt、lt、ge、le|PID 値|
|SESSION|eq、ne、gt、lt、ge、le|セッション番号|
|セッション名|eq、ne|Session name (セッション名)|
|CPU 時間 値|eq、ne、gt、lt、ge、le|CPU 時間の形式で*HH ***:*** MM ***:*** SS*ここで、 *MM*と*SS*は 0 と 59 ~*HH*は符号なしのいずれかの数|
|MEMUSAGE|eq、ne、gt、lt、ge、le|メモリの使用量 (KB 単位)|
|USERNAME|eq、ne|任意の有効なユーザー名|
|サービス|eq、ne|サービス名|
|WINDOWTITLE|eq、ne|ウィンドウのタイトル|
|モジュール|eq、ne|DLL 名|

## <a name="remarks"></a>注釈

リモート システムが指定されているときに、WINDOWTITLE と状態のフィルターはサポートされていません。

## <a name="BKMK_examples"></a>例

プロセス id が 1000 を超えるすべてのタスクの一覧を CSV 形式で表示するには、次のように入力します。
```
tasklist /v /fi "PID gt 1000" /fo csv
```
現在実行されているシステム プロセスを一覧表示するには、次のように入力します。
```
tasklist /fi "USERNAME ne NT AUTHORITY\SYSTEM" /fi "STATUS eq running"
```
現在実行されているすべてのプロセスの詳細情報を一覧表示するには、次のように入力します。
```
tasklist /v /fi "STATUS eq running"
```
"Srvmain"を"ntdll"で始まるを DLL 名を持つリモート コンピューター上のプロセスのすべてのサービス情報を一覧表示するには、次のように入力します。
```
tasklist /s srvmain /svc /fi "MODULES eq ntdll*"
```
"Srvmain、"、現在ログオンしているユーザー アカウントの資格情報を使用してリモート コンピューター上のプロセスを一覧表示するには、次のように入力します。
```
tasklist /s srvmain 
```
"Srvmain、"Hiropln、ユーザー アカウントの資格情報を使用してリモート コンピューター上のプロセスを一覧表示するには、次のように入力します。
```
tasklist /s srvmain /u maindom\hiropln /p p@ssW23
```

#### <a name="additional-references"></a>その他の参照情報

[コマンドライン構文キー](command-line-syntax-key.md)