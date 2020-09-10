---
title: bitsadmin getcustomheaders
description: Bitsadmin getcustomheaders コマンドの参照記事で、ジョブからカスタム HTTP ヘッダーを取得します。
ms.topic: reference
ms.assetid: 1f0d38d3-e865-4474-81e8-773d65c3d1cc
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ec061c9e7f195d463525031bcbefc97913d69083
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632196"
---
# <a name="bitsadmin-getcustomheaders"></a>bitsadmin getcustomheaders

ジョブからカスタム HTTP ヘッダーを取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getcustomheaders <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのカスタムヘッダーを取得するには、次のようにします。

```
bitsadmin /getcustomheaders myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
