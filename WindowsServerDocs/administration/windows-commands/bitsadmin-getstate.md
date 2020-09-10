---
title: bitsadmin getstate
description: Bitsadmin getstate コマンドの参照記事。指定されたジョブの状態を取得します。
ms.topic: reference
ms.assetid: 1252d6cf-14ca-44df-beb2-930ff011f297
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2faf05bd245f0b59eb9f10d0d46d96e8e1d3e11c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631655"
---
# <a name="bitsadmin-getstate"></a>bitsadmin getstate

指定されたジョブの状態を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getstate <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

#### <a name="output"></a>出力

返される出力値は次のようになります。

| State | Description |
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
