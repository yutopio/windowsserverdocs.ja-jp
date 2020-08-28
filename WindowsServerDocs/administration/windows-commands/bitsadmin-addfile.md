---
title: bitsadmin addfile
description: Bitsadmin addfile コマンドの参照記事。指定されたジョブにファイルを追加します。
ms.topic: reference
ms.assetid: 1b31aa93-0364-465b-af36-754968825989
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 63df6c33bae3022c91633d4507c1fe9709cdd65e
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89031380"
---
# <a name="bitsadmin-addfile"></a>bitsadmin addfile

指定されたジョブにファイルを追加します。

## <a name="syntax"></a>構文

```
bitsadmin /addfile <job> <remoteURL> <localname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| remoteURL | サーバー上のファイルの URL。 |
| localname | ローカルコンピューター上のファイルの名前。 *Localname* には、ファイルへの絶対パスが含まれている必要があります。 |

## <a name="examples"></a>例

ジョブにファイルを追加するには、次のようにします。

```
bitsadmin /addfile myDownloadJob http://downloadsrv/10mb.zip c:\10mb.zip
```

追加する各ファイルに対してこの呼び出しを繰り返します。 複数のジョブが *Mydownloadjob* を名前として使用する場合は、ジョブを一意に識別するために、 *mydownloadjob* をジョブの GUID に置き換える必要があります。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
