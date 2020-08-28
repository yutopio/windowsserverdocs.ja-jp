---
title: セットのメタデータ
description: 設定メタデータの参照記事。シャドウコピーを別のコンピューターに転送するために使用するシャドウ作成メタデータファイルの名前と場所を設定します。
ms.topic: reference
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dabec963b84a5c8d5acfd5e214b8d62d4740d9b3
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024946"
---
# <a name="set-metadata"></a>セットのメタデータ

シャドウ コピーを別の 1 台のコンピューターに転送するために使用したシャドウの作成のメタデータ ファイルの場所と名前を設定します。 パラメーターを指定せずに使用する場合 **メタデータ設定** コマンド プロンプトでヘルプを表示します。

## <a name="syntax"></a>構文

```
set metadata [<Drive>:][<Path>]<MetaData.cab>
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|[\<Drive>:][<Path>]|メタデータ ファイルを作成する場所を指定します。|
|\<MetaData.cab>|シャドウの作成のメタデータを格納する cab ファイルの名前を指定します。|

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)