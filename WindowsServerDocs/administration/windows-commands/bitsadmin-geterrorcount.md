---
title: bitsadmin geterrorcount
description: Bitsadmin geterrorcount コマンドの参照記事。指定されたジョブが一時的なエラーを生成した回数のカウントを取得します。
ms.topic: reference
ms.assetid: 8840ae78-52b0-4c7e-b592-0547359a237e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7266af9244218cf4a6434c838390eac8149c80ab
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632115"
---
# <a name="bitsadmin-geterrorcount"></a>bitsadmin geterrorcount

指定したジョブが一時的なエラーを生成した回数のカウントを取得します。

## <a name="syntax"></a>構文

```
bitsadmin /geterrorcount <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのエラー数情報を取得するには、次のようにします。

```
bitsadmin /geterrorcount myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
