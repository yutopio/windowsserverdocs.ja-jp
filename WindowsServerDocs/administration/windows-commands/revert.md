---
title: 反転
description: 元に戻すコマンドの参照記事。ボリュームを指定したシャドウコピーに戻します。
ms.topic: reference
ms.assetid: 75ad40e4-502a-401e-b11e-8b31e00424b5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3c909cec1e503552f68cad55489529585a5eaf51
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640625"
---
# <a name="revert"></a>反転

指定したシャドウ コピーにボリュームを元に戻します。 これは CLIENTACCESSIBLE コンテキストでのシャドウ コピーに対してのみサポートされます。 これらのシャドウ コピーは、永続的なシステム プロバイダーによってのみ実行できます。 パラメーターを指定せずに使用する場合 **を元に戻す** コマンド プロンプトでヘルプを表示します。

## <a name="syntax"></a>構文

```
revert <shadowcopyID>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<shadowcopyID>` | ボリュームを元に戻すシャドウ コピー ID を指定します。 このパラメーターを使用しない場合は、コマンドプロンプトでヘルプが表示されます。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
