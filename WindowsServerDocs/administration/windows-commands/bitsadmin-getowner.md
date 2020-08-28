---
title: bitsadmin getowner
description: Bitsadmin getowner コマンドの参照記事。指定されたジョブの所有者を取得します。
ms.topic: reference
ms.assetid: 5203f84c-a879-4f31-ae3e-7ea74bd63ca5
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1100ac3e126c1186ac498c0ee17831cbd2c6a694
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028710"
---
# <a name="bitsadmin-getowner"></a>bitsadmin getowner

指定したジョブの所有者の表示名または GUID が表示されます。

## <a name="syntax"></a>構文

```
bitsadmin /getowner <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの所有者を表示するには、次のようにします。

```
bitsadmin /getowner myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
