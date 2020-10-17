---
title: ver
description: オペレーティングシステムのバージョン番号を表示する ver コマンドの参照記事です。
ms.topic: reference
ms.assetid: 5a9c6cd4-b67d-4b30-8c56-5f9798eafd2a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9e99c5af9ee45b33cb0c050307c83c89874d89cb
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156274"
---
# <a name="ver"></a>ver

オペレーティング システムのバージョン番号を表示します。 このコマンドは、Windows コマンドプロンプト (Cmd.exe) でサポートされていますが、PowerShell ではサポートされていません。

## <a name="syntax"></a>構文

```
ver
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>使用例

コマンドシェル (cmd.exe) からオペレーティングシステムのバージョン番号を取得するには、次のように入力します。

```
ver
```

**Ver**コマンドは PowerShell では機能しません。 PowerShell を使用してオペレーティングシステムのバージョン番号を取得するには、次のように入力します。

```powershell
$PSVersionTable.BuildVersion
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
