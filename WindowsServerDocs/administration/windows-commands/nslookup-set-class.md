---
title: nslookup set class
description: Nslookup set class コマンドの参照記事。クエリクラスを変更します。
ms.topic: reference
ms.assetid: ed826400-40da-42b6-b7f0-95db73790723
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5f4eb309c3972230247bf231b0e731e146d8159a
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89634037"
---
# <a name="nslookup-set-class"></a>nslookup set class

クエリクラスを変更します。 クラスは、情報のプロトコルグループを指定します。

## <a name="syntax"></a>構文

```
set class=<class>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<class>` | 有効な値は次のとおりです。<ul><li>**:** インターネットクラスを指定します。 これが既定値です。</li><li>**混乱:** 混乱クラスを指定します。</li><li>**HESIOD:** MIT アテナ Hesiod クラスを指定します。</li><li>**任意:** 以前に一覧表示された値のいずれかを使用するように指定します。</li></ul> |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
