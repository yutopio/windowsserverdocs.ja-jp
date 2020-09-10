---
title: bitsadmin getclientcertificate
description: Bitsadmin getclientcertificate コマンドの参照記事で、ジョブからクライアント証明書を取得します。
ms.topic: reference
ms.assetid: 4fc8f408-085e-43a0-9fa8-3d798ef107b1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 71f1ed8920ba2bd3aa0a0f48683d8841e08afb6d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632260"
---
# <a name="bitsadmin-getclientcertificate"></a>bitsadmin getclientcertificate

ジョブからクライアント証明書を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getclientcertificate <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのクライアント証明書を取得するには、次のようにします。

```
bitsadmin /getclientcertificate myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
