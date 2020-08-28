---
title: bitsadmin setpriority
description: 指定されたジョブの優先度を設定する bitsadmin setpriority コマンドの参照記事です。
ms.topic: reference
ms.assetid: 90788363-01a2-4d7c-a560-a3eba45b5e9e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b1fe6a2b3981697a4a8c287fe4fb49c31a4f4244
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028470"
---
# <a name="bitsadmin-setpriority"></a>bitsadmin setpriority

指定されたジョブの優先順位を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setpriority <job> <priority>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| priority | ジョブの優先順位を設定します。次に例を示します。<ul><li>FOREGROUND</li><li>HIGH</li><li>NORMAL</li><li>LOW</li></ul> |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの優先順位を normal に設定するには、次のようにします。

```
bitsadmin /setpriority myDownloadJob NORMAL
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
