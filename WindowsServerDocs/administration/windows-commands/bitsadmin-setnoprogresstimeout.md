---
title: bitsadmin setnoprogresstimeout
description: Bitsadmin setnoprogresstimeout コマンドの参照記事では、一時的なエラーが発生した後にサービスがファイルの転送を試行する時間を秒単位で設定します。
ms.topic: reference
ms.assetid: 7fac50d9-cc6b-46a4-a96f-fab751ee1756
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9ffe7280e6a27d1fbc8a95b6b4c8375a8df844f8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630804"
---
# <a name="bitsadmin-setnoprogresstimeout"></a>bitsadmin setnoprogresstimeout

最初の一時的なエラーが発生した後に、BITS がファイルの転送を試行する時間を秒単位で設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setnoprogresstimeout <job> <timeoutvalue>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| timeoutvalue | 最初のエラーの後、ファイルの転送を BITS が待機する時間 (秒単位)。 |

### <a name="remarks"></a>注釈

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
