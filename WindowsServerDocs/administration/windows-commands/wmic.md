---
title: wmic
description: 対話型コマンドシェル内に WMI 情報を表示する wmic のリファレンス記事です。
ms.topic: reference
ms.assetid: 76397c72-d06f-4cea-88cf-c7603315a983
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d79f00798b3901d1b8cc44d313824130b1c8fb62
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638867"
---
# <a name="wmic"></a>wmic



対話型コマンドシェル内に WMI 情報を表示します。



## <a name="syntax"></a>Syntax

```
wmic </parameter>
```

## <a name="sub-commands"></a>サブコマンド

次のサブコマンドは常に使用できます。

|サブコマンド|説明|
|-----------|-----------|
|class|WMIC の既定のエイリアスモードをエスケープして、WMI スキーマ内のクラスに直接アクセスします。|
|path|WMIC の既定のエイリアスモードをエスケープして、WMI スキーマ内のインスタンスに直接アクセスできるようにします。|
|context|すべてのグローバルスイッチの現在の値を表示します。|
|[終了 \| 終了]|WMIC コマンドシェルを終了します。|

## <a name="examples"></a>例

すべてのグローバルスイッチの現在の値を表示するには、次のように入力します。
```
wmic context
```
次のような出力が表示されます。
```
NAMESPACE    : root\cimv2
ROLE         : root\cli
NODE(S)      : BOBENTERPRISE
IMPLEVEL     : IMPERSONATE
[AUTHORITY   : N/A]
AUTHLEVEL    : PKTPRIVACY
LOCALE       : ms_409
PRIVILEGES   : ENABLE
TRACE        : OFF
RECORD       : N/A
INTERACTIVE  : OFF
FAILFAST     : OFF
OUTPUT       : STDOUT
APPEND       : STDOUT
USER         : N/A
AGGREGATE    : ON
```
コマンドラインで使用される言語 ID を英語 (ロケール ID 409) に変更するには、次のように入力します。
```
wmic /locale:ms_409
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
