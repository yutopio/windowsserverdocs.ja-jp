---
title: bitsadmin getstate
description: Bitsadmin getstate コマンドの参照記事。指定されたジョブの状態を取得します。
ms.topic: reference
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 7267afde1062c1b8d3383ea92f02d18728650136
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89034820"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate

指定されたジョブの状態を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getstate <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

#### <a name="output"></a>Output

返される出力値は次のようになります。

| State | 説明 |
| --------------- | ----------- |
| キューに登録済み | ジョブは実行を待機しています。 |
| 接続 | BITS はサーバーに接続しています。 |
| 転送 | BITS はデータを転送しています。 |
| 支払 | BITS によってジョブ内のすべてのファイルが正常に転送されました。 |
| Suspended | ジョブが一時停止されています。 |
| エラー | 回復不可能なエラーが発生しました。転送は再試行されません。 |
| Transient_Error | 回復可能なエラーが発生しました。最小再試行間隔が経過すると、転送が再試行されます。 |
| [Acknowledged] (確認済み) | ジョブが完了しました。 |
| Canceled | ジョブは取り消されました。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの状態を取得するには、次のようにします。

```
bitsadmin /getstate myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
