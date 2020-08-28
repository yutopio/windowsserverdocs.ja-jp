---
title: bitsadmin setnoprogresstimeout
description: Bitsadmin setnoprogresstimeout コマンドの参照記事では、一時的なエラーが発生した後にサービスがファイルの転送を試行する時間を秒単位で設定します。
ms.topic: reference
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: dc2559a963900234fd3111edb1a32e3f13b27e40
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027800"
---
# <a name="bitsadmin-setnoprogresstimeout"></a>bitsadmin setnoprogresstimeout

最初の一時的なエラーが発生した後に、BITS がファイルの転送を試行する時間を秒単位で設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setnoprogresstimeout <job> <timeoutvalue>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| timeoutvalue | 最初のエラーの後、ファイルの転送を BITS が待機する時間 (秒単位)。 |

### <a name="remarks"></a>解説

- ジョブが最初の一時的なエラーを検出したときに、"進行状況なし" のタイムアウト間隔が開始されます。

- データのバイトが正常に転送されると、タイムアウト間隔が停止またはリセットされます。

- "進行状況なし" のタイムアウト間隔が *timeoutvalue*を超えると、ジョブは致命的なエラー状態になります。

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの "進行状況なし" タイムアウト値を20秒に設定するには、次のようにします。

```
bitsadmin /setnoprogresstimeout myDownloadJob 20
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
