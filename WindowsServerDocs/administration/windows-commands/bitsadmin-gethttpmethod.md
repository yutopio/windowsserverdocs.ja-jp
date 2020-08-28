---
title: bitsadmin gethttpmethod
description: ジョブで使用する HTTP 動詞を取得する bitsadmin gethttpmethod コマンドの参照記事です。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 5bbd2509cabea7ae68240a31cee78d9ffd3ac5e0
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033530"
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
