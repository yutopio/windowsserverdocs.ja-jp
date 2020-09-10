---
title: bitsadmin getnoprogresstimeout
description: Bitsadmin getnoprogresstimeout コマンドの参照記事。一時的なエラーが発生した後に、サービスがファイルの転送を試行する時間 (秒単位) を取得します。
ms.topic: reference
ms.assetid: 9cd9b19b-cbb4-4352-8419-978080f016b6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a7f5a84b90f124cb172ad551b196cac152a332a8
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631918"
---
# <a name="bitsadmin-getnoprogresstimeout"></a>bitsadmin getnoprogresstimeout

一時的なエラーが発生した後に、サービスがファイルの転送を試行する時間 (秒単位) を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getnoprogresstimeout <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの進行状況のタイムアウト値を取得するには、次のようにします。

```
bitsadmin /getnoprogresstimeout myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
