---
title: bitsadmin suspend
description: Bitsadmin suspend コマンドの参照記事。指定されたジョブを中断します。
ms.topic: reference
ms.assetid: f9d42500-7bea-4aa8-a9f0-c22f6ed3e73b
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: ad4ca877ac9e5548f3d3ec830f8fc2822f781218
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033390"
---
# <a name="bitsadmin-suspend"></a>bitsadmin suspend

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定されたジョブを中断します。 誤ってジョブを中断した場合は、 [bitsadmin resume](bitsadmin-resume.md) スイッチを使用してジョブを再開できます。

## <a name="syntax"></a>構文

```
bitsadmin /suspend <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ---------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="example"></a>例

*Mydownloadjob*という名前のジョブを中断するには、次のようにします。


```
bitsadmin /suspend myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin resume コマンド](bitsadmin-resume.md)

- [bitsadmin コマンド](bitsadmin.md)
