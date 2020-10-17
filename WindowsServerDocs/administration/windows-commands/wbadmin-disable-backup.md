---
title: wbadmin disable backup
description: 既存のスケジュールされた毎日のバックアップの実行を停止する wbadmin disable backup コマンドの参照記事です。
ms.topic: reference
ms.assetid: 5176cbd9-0696-4b3f-9c35-272dd84f7898
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f490ede3b6f48285291b1658458d8c8c176bb2c8
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156046"
---
# <a name="wbadmin-disable-backup"></a>wbadmin disable backup

既存のスケジュールされた毎日のバックアップの実行を停止します。

このコマンドを使用して、スケジュールされた毎日のバックアップを無効にするには、 **Administrators** グループのメンバーであるか、適切な権限が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

## <a name="syntax"></a>構文

```
wbadmin disable backup [-quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [wbadmin enable backup コマンド](wbadmin-enable-backup.md)