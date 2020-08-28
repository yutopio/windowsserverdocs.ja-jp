---
title: bitsadmin setminretrydelay
description: Bitsadmin setminretrydelay コマンドの参照記事。このコマンドは、ファイルの転送を試行する前に、一時的なエラーが発生した後に BITS が待機する最小時間を秒単位で設定します。
ms.topic: reference
ms.assetid: ce8674ca-6cc5-4bb2-8dda-7dfbb1cd6830
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5ef8ed52e991ae9c2d1807ade604cc0cab066743
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031270"
---
# <a name="bitsadmin-setminretrydelay"></a>bitsadmin setminretrydelay

一時エラーが発生してからファイルの転送を試行するまでの待機時間の最小値を秒単位で設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setminretrydelay <job> <retrydelay>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| retrydelay | 転送中にエラーが発生した後のビットの待機時間の最小値 (秒単位)。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの最小再試行間隔を35秒に設定するには、次のようにします。

```
bitsadmin /setminretrydelay myDownloadJob 35
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
