---
title: serverceipoptin
description: 参照記事 * * * *-
ms.topic: reference
ms.assetid: 3d7d7fa7-0689-4797-b802-36fe260d21a0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 691b2e072d6581f8f8760e20d4ba8f09500ed169
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638980"
---
# <a name="serverceipoptin"></a>serverceipoptin

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

カスタマー エクスペリエンス向上プログラム (CEIP) に参加できます。
## <a name="syntax"></a>構文
```
serverceipoptin [/query] [/enable] [/disable]
```
#### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|/query|現在の設定を検証します。|
|/enable|参加を有効にします。|
|/disable|参加を無効にします。|
|/?|コマンド プロンプトにヘルプを表示します。|
## <a name="examples"></a>例
現在の設定を確認するには、次のように入力します。
```
serverceipoptin /query
```
参加を有効にするには、次のように入力します。
```
serverceipoptin /enable
```
参加を無効にするには、次のように入力します。
```
serverceipoptin /disable
```
## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)

