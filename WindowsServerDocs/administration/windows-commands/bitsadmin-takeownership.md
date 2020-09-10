---
title: bitsadmin takeownership
description: 管理者特権を持つユーザーが、指定されたジョブの所有権を取得できるようにする bitsadmin の所有権の取得コマンドに関するリファレンス記事です。
ms.topic: reference
ms.assetid: ea0ce7cb-440a-498f-a3ef-8368fa43e399
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a4998ce3c28c839bb035a04c5472aae7c98b4eac
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630576"
---
# <a name="bitsadmin-takeownership"></a>bitsadmin takeownership

管理者特権を持つユーザーが、指定されたジョブの所有権を取得できるようにします。

## <a name="syntax"></a>構文

```
bitsadmin /takeownership <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ---------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの所有権を取得するには、次のようにします。

```
bitsadmin /takeownership myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
