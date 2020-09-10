---
title: セットのメタデータ
description: 設定メタデータの参照記事。シャドウコピーを別のコンピューターに転送するために使用するシャドウ作成メタデータファイルの名前と場所を設定します。
ms.topic: reference
ms.assetid: 67e6f60a-b42a-451a-95cf-b22ace7d50c2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b680ac538f7c2593871137b07d045ef150b68b1f
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637683"
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