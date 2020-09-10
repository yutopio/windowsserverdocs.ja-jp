---
title: bitsadmin complete
description: ジョブを完了する bitsadmin complete コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: a5e86677-8f7b-43b3-929e-97706c57e7f1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 88e8ac3920adb80dcc453317fbffe5fd661811fb
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632384"
---
# <a name="bitsadmin-complete"></a>bitsadmin complete

ジョブを完了します。 ジョブが転送済み状態に移行した後に、このスイッチを使用します。 そうしないと、正常に転送されたファイルのみが使用可能になります。

## <a name="syntax"></a>構文

```
bitsadmin /complete <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="example"></a>例

*Mydownloadjob*ジョブを完了するには、次のようにし `TRANSFERRED` ます。

```
bitsadmin /complete myDownloadJob
```

複数のジョブが *Mydownloadjob* を名前として使用している場合は、ジョブの GUID を使用して、ジョブの完了を一意に識別する必要があります。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
