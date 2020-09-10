---
title: bitsadmin gethttpmethod
description: ジョブで使用する HTTP 動詞を取得する bitsadmin gethttpmethod コマンドの参照記事です。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 0d96c85aa99330b133954a77ca5584fe2d02cd43
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632033"
---
# <a name="bitsadmin-gethttpmethod"></a>bitsadmin gethttpmethod

ジョブで使用する HTTP 動詞を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /gethttpmethod <Job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブで使用する HTTP 動詞を取得するには、次のようにします。

```
bitsadmin /gethttpmethod myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
