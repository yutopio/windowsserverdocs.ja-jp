---
title: wbadmin disable backup
description: 既存のスケジュールされた毎日のバックアップの実行を停止する wbadmin disable backup のリファレンス記事です。
ms.topic: reference
ms.assetid: 5176cbd9-0696-4b3f-9c35-272dd84f7898
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5525dc4c62900f2f250fc36670f83cefd0b55e35
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640758"
---
# <a name="wbadmin-disable-backup"></a>wbadmin disable backup



既存のスケジュールされた毎日のバックアップの実行を停止します。

スケジュールされた毎日のバックアップを無効にするには、 **Administrators** グループのメンバーであるか、適切な権限が委任されている必要があります。 さらに、実行する必要があります **wbadmin** 管理者特権でコマンド プロンプトからです。 (管理者特権でのコマンドプロンプトを開くには、[ **コマンドプロンプト** ] を右クリックし、[ **管理者として実行**] をクリックします)。

## <a name="syntax"></a>構文

```
wbadmin disable backup
[-quiet]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|-quiet|ユーザーにプロンプトを表示せずにサブコマンドを実行します。|

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)