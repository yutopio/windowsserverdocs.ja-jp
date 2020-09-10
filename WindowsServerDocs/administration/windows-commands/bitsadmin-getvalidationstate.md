---
title: bitsadmin getvalidationstate
description: Bitsadmin getvalidationstate コマンドの参照記事。ジョブ内の指定されたファイルのコンテンツ検証の状態を報告します。
ms.topic: reference
ms.assetid: 6ada3f1f-9967-4262-9d22-ed641e23f516
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5f85f006efa18baa95a491b84e365e707cdf225c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631550"
---
# <a name="bitsadmin-getvalidationstate"></a>bitsadmin getvalidationstate

ジョブ内の指定されたファイルのコンテンツ検証の状態を報告します。

## <a name="syntax"></a>構文

```
bitsadmin /getvalidationstate <job> <file_index>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| file_index | 0から開始します。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブ内のファイル2のコンテンツの検証状態を取得するには、次のようにします。

```
bitsadmin /getvalidationstate myDownloadJob 1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
