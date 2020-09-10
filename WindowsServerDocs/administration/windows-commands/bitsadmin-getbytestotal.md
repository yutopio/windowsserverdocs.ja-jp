---
title: bitsadmin getbytestotal
description: 指定されたジョブのサイズを取得する bitsadmin getbytestotal コマンドの参照記事です。
ms.topic: reference
ms.assetid: 784e0bfa-7b09-4262-9104-adbc9beb479b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 50b926b8d89e402ef4fd9e58896963edd3c368c9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632344"
---
# <a name="bitsadmin-getbytestotal"></a>bitsadmin getbytestotal

指定されたジョブのサイズを取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getbytestotal <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのサイズを取得するには、次のようにします。

```
bitsadmin /getbytestotal myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
