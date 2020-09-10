---
title: bitsadmin util および version
description: BITS サービスのバージョンを表示する bitsadmin util と version コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 98f17328-dfbd-4cbb-93c1-b8d424bc3f0a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 783b709840070847c90bbf9d2b4aebc0758a5742
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630417"
---
# <a name="bitsadmin-util-and-version"></a>bitsadmin util および version

BITS サービスのバージョン (2.0 など) を表示します。

> [!NOTE]
> このコマンドは、BITS 1.5 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /util /version [/verbose]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| /verbose | このスイッチを使用して、BITS 関連の各 DLL のファイルバージョンを表示し、BITS サービスを開始できるかどうかを確認します。|

## <a name="examples"></a>例

BITS サービスのバージョンを表示します。

```
bitsadmin /util /version
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin util コマンド](bitsadmin-util.md)

- [bitsadmin コマンド](bitsadmin.md)
