---
title: bitsadmin getvalidationstate
description: Bitsadmin getvalidationstate コマンドの参照記事。ジョブ内の指定されたファイルのコンテンツ検証の状態を報告します。
ms.topic: reference
ms.assetid: 6ada3f1f-9967-4262-9d22-ed641e23f516
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 173bbaad6508ec3ae8100232fda598fe7a422296
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028640"
---
# <a name="bitsadmin-getvalidationstate"></a>bitsadmin getvalidationstate

ジョブ内の指定されたファイルのコンテンツ検証の状態を報告します。

## <a name="syntax"></a>構文

```
bitsadmin /getvalidationstate <job> <file_index>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
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
