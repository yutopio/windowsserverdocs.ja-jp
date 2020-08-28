---
title: bitsadmin setcustomheaders
description: Bitsadmin setcustomheaders コマンドの参照記事。 GET 要求にカスタム HTTP ヘッダーを追加します。
ms.topic: reference
ms.assetid: ed926410-80d0-46ed-9a90-f752c164bb9a
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 84622cba8bb2bcb6a9ebfe782fdadc33a388fdb2
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031280"
---
# <a name="bitsadmin-setcustomheaders"></a>bitsadmin setcustomheaders

HTTP サーバーに送信される GET 要求にカスタム HTTP ヘッダーを追加します。 GET 要求の詳細については、「 [メソッドの定義](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html#sec9.3) 」および「 [ヘッダーフィールドの定義](https://www.w3.org/Protocols/rfc2616/rfc2616-sec14.html)」を参照してください。

## <a name="syntax"></a>構文

```
bitsadmin /setcustomheaders <job> <header1> <header2> <...>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| `<header1> <header2>` などなど | ジョブのカスタムヘッダー。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのカスタム HTTP ヘッダーを追加するには、次のようにします。

```
bitsadmin /setcustomheaders myDownloadJob accept-encoding:deflate/gzip
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
