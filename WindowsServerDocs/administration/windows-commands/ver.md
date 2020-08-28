---
title: ver
description: オペレーティングシステムのバージョン番号を表示する ver のリファレンス記事です。
ms.topic: reference
ms.assetid: 5a9c6cd4-b67d-4b30-8c56-5f9798eafd2a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 543aceee52be60b6dc90509c326ba1172b2d1ca6
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023046"
---
# <a name="ver"></a>ver



オペレーティング システムのバージョン番号を表示します。

このコマンドは、Windows コマンドプロンプト (Cmd.exe) でサポートされていますが、PowerShell ではサポートされていません。



## <a name="syntax"></a>構文

```
ver
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="examples"></a>例

コマンドシェル (cmd.exe) からオペレーティングシステムのバージョン番号を取得するには、次のように入力します。

```
ver
```

Ver コマンドは PowerShell では機能しません。 PowerShell から OS バージョンを取得するには、次のように入力します。

```powershell
$PSVersionTable.BuildVersion
````


## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
