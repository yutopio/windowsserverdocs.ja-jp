---
title: bitsadmin getclientcertificate
description: Bitsadmin getclientcertificate コマンドの参照記事で、ジョブからクライアント証明書を取得します。
ms.topic: reference
ms.assetid: 4fc8f408-085e-43a0-9fa8-3d798ef107b1
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5a2fe63369aab098b012462e063518463047218d
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027830"
---
# <a name="bitsadmin-getclientcertificate"></a>bitsadmin getclientcertificate

ジョブからクライアント証明書を取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getclientcertificate <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
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
