---
title: bitsadmin getsecurityflags
description: Bitsadmin getsecurityflags コマンドのリファレンス記事。転送中にサーバー証明書に対して実行される URL リダイレクトとチェックの HTTP セキュリティフラグを報告します。
ms.topic: reference
ms.assetid: c2e73519-34f4-487b-af11-97d5d08ef9bb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ce0637527b39ebf05546b62671ce11a87151b572
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631703"
---
# <a name="bitsadmin-getsecurityflags"></a>bitsadmin getsecurityflags

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

転送中にサーバー証明書に対して実行された URL リダイレクトおよび確認の HTTP セキュリティフラグを報告します。

## <a name="syntax"></a>構文

```
bitsadmin /getsecurityflags <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブからセキュリティフラグを取得するには、次のようにします。

```
bitsadmin /getsecurityflags myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
