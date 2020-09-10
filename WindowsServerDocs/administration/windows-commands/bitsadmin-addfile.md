---
title: bitsadmin addfile
description: Bitsadmin addfile コマンドの参照記事。指定されたジョブにファイルを追加します。
ms.topic: reference
ms.assetid: 1b31aa93-0364-465b-af36-754968825989
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 74e77f2af220a057ed0ad87da797e9ae88c7aef5
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632740"
---
# <a name="bitsadmin-addfile"></a>bitsadmin addfile

指定されたジョブにファイルを追加します。

## <a name="syntax"></a>構文

```
bitsadmin /addfile <job> <remoteURL> <localname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
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
