---
title: mask
description: Mask コマンドの参照記事。 import コマンドを使用してインポートされたハードウェアシャドウコピーを削除します。
ms.topic: reference
ms.assetid: bf301474-d74a-44e7-9fad-c8a11e7ca3bd
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: c5d8f86de3019e47da3aff56aa370972de3288fa
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037870"
---
# <a name="mask"></a>mask

**インポート**コマンドを使用してインポートされたハードウェアシャドウコピーを削除します。

## <a name="syntax"></a>構文

```
mask <shadowsetID>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| shadowsetID | 指定されたシャドウコピーセット ID に属するシャドウコピーを削除します。 |

#### <a name="remarks"></a>解説

- *ShadowSetID*の代わりに、既存のエイリアスまたは環境変数を使用できます。 既存のエイリアスを表示するには、パラメーターを指定せずに **add** を使用します。

### <a name="examples"></a>例

インポートされたシャドウコピー *% Import_1%* を削除するには、次のように入力します。

```
mask %Import_1%
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)