---
title: bitsadmin setvalidationstate
description: Bitsadmin setvalidationstate コマンドの参照記事。このコマンドは、ジョブ内の指定されたファイルのコンテンツ検証の状態を設定します。
ms.topic: reference
ms.assetid: e8fc8e8c-171c-4681-8057-6986b018e576
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1f30807e392ede7710c4d7740416d2cdb34c1378
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630609"
---
# <a name="bitsadmin-setvalidationstate"></a>bitsadmin setvalidationstate

ジョブ内の指定されたファイルのコンテンツ検証の状態を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setvalidationstate <job> <file_index> <TRUE|FALSE>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ---------- |
| ジョブ | ジョブの表示名または GUID。 |
| file_index | 0から開始します。 |
| TRUE または FALSE | **TRUE** を指定すると、指定したファイルのコンテンツの検証が有効になり、 **FALSE** の場合は無効になります。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブについて、ファイル2のコンテンツの検証の状態を TRUE に設定するには、次のようにします。

```
bitsadmin /setvalidationstate myDownloadJob 2 TRUE
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
