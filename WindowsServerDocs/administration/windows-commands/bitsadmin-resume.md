---
title: bitsadmin resume
description: Bitsadmin resume コマンドの参照記事。転送キューで新規または中断されたジョブをアクティブ化します。
ms.topic: reference
ms.assetid: 7c7540a9-a11a-4910-923a-2a2a61cbf11d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2ccab242034af3e0b5e01f0efec60d5309879516
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89631104"
---
# <a name="bitsadmin-resume"></a>bitsadmin resume

転送キューで新規または中断されたジョブをアクティブにします。 ジョブを誤って再開した場合、または単にジョブを中断する必要がある場合は、 [bitsadmin suspend](bitsadmin-suspend.md) スイッチを使用してジョブを中断できます。

## <a name="syntax"></a>構文

```
bitsadmin /resume <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブを再開するには、次のようにします。

```
bitsadmin /resume myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin suspend コマンド](bitsadmin-suspend.md)

- [bitsadmin コマンド](bitsadmin.md)
