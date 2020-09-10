---
title: bitsadmin reset
description: Bitsadmin reset コマンドの参照記事。現在のユーザーが所有している転送キュー内のすべてのジョブを取り消します。
ms.topic: reference
ms.assetid: 0e4f9d1d-072c-493f-8d7a-f6d713c3ef29
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: baf7aa52c92be35c1439d1fbfaa1e7409b58dcd9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631114"
---
# <a name="bitsadmin-reset"></a>bitsadmin reset

現在のユーザーが所有している転送キュー内のすべてのジョブをキャンセルします。 ローカルシステムによって作成されたジョブをリセットすることはできません。 代わりに、管理者である必要があります。また、タスクスケジューラを使用して、ローカルシステムの資格情報を使用して、このコマンドをタスクとしてスケジュールする必要があります。

> [!NOTE]
> BITSAdmin 1.5 以前の管理者特権を持っている場合、/reset スイッチを使用すると、キュー内のすべてのジョブが取り消されます。 また、/allusers オプションはサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /reset [/allusers]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| /allusers | 省略可能。 現在のユーザーが所有しているキュー内のすべてのジョブをキャンセルします。 このパラメーターを使用するには、管理者特権が必要です。 |

## <a name="examples"></a>例

現在のユーザーの転送キューにあるすべてのジョブを取り消す場合はです。

```
bitsadmin /reset
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
