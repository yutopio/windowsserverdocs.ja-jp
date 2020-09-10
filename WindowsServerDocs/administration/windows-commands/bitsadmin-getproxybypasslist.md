---
title: bitsadmin getproxybypasslist
description: Bitsadmin getproxybypasslist コマンドの参照記事。指定されたジョブのプロキシバイパスリストを取得します。
ms.topic: reference
ms.assetid: 50959be3-7014-4bc9-9a7b-68f1ff94a94a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5b9b9ffd3865ef70408c566bdd832005e74f6598
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631754"
---
# <a name="bitsadmin-getproxybypasslist"></a>bitsadmin getproxybypasslist

指定されたジョブのプロキシバイパスリストを取得します。

## <a name="syntax"></a>構文

```
bitsadmin /getproxybypasslist <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

### <a name="remarks"></a>注釈

バイパスリストには、プロキシ経由でルーティングされないホスト名または IP アドレス (またはその両方) が含まれます。 この一覧には、 `<local>` 同じ LAN 上のすべてのサーバーを参照するを含めることができます。 リストはセミコロン (;)またはスペースで区切られます。

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのプロキシバイパス一覧を取得するには、次のようにします。

```
bitsadmin /getproxybypasslist myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
