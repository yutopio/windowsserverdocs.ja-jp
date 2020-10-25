---
title: wbadmin stop job
description: Wbadmin stop job コマンドの参照記事。現在実行中のバックアップまたは回復操作をキャンセルします。
ms.topic: reference
ms.assetid: 3b83b398-39c7-4410-bf17-5c1fb1a4f46d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9952f28f674da6eae295dcffc0357cade19fdd1c
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524707"
---
# <a name="wbadmin-stop-job"></a>wbadmin stop job

現在実行中のバックアップまたは回復操作をキャンセルします。

> [!IMPORTANT]
> 取り消された操作を再開することはできません。 取り消されたバックアップまたは回復操作は、もう一度最初から実行する必要があります。

このコマンドを使用してバックアップまたは回復操作を停止するには、 **Backup Operators** グループまたは **Administrators** グループのメンバーであるか、適切なアクセス許可が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

## <a name="syntax"></a>構文

```
wbadmin stop job [-quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)
