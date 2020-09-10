---
title: bitsadmin getnotifycmdline
description: Bitsadmin getnotifycmdline コマンドの参照記事。ジョブがデータの転送を終了したときに実行されるコマンドラインコマンドを取得します。
ms.topic: reference
ms.assetid: 90fa33e6-aca5-4a23-82bd-19a9f13f8416
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 26b2f50520f0b77f5792b279513caedaf560eea9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631924"
---
# <a name="bitsadmin-getnotifycmdline"></a>bitsadmin getnotifycmdline

指定されたジョブがデータの転送を終了した後に実行するコマンドラインコマンドを取得します。

> [!NOTE]
> このコマンドは、BITS 1.2 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /getnotifycmdline <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブが完了したときにサービスによって使用されるコマンドラインコマンドを取得すること。

```
bitsadmin /getnotifycmdline myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
