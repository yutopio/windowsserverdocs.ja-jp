---
title: scwcmd view
description: Scwcmd view コマンドの参照記事。指定した .xsl 変換を使用して .xml ファイルを表示します。
ms.topic: reference
ms.assetid: 7995959a-d93e-4865-a6a0-2ab18c2bb47f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e411bf06015684e7dedb94d109f5e4294f46af84
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388932"
---
# <a name="scwcmd-view"></a>scwcmd view

> 適用対象: Windows Server 2012 R2 および Windows Server 2012

指定した .xsl 変換を使用して .xml ファイルを表示します。 このコマンドは、さまざまなビューを使用して、.xml ファイルのセキュリティ構成ウィザード (SCW) を表示するために役立ちます。

## <a name="syntax"></a>構文

```
scwcmd view /x:<Xmlfile.xml> [/s:<Xslfile.xsl>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| x`<Xmlfile.xml>` | 表示する .xml ファイルを指定します。 このパラメーターを指定する必要があります。 |
| /s`<Xslfile.xsl>` | レンダリング プロセスの一環として、.xml ファイルに適用する .xsl 変換を指定します。 このパラメーターは、SCW の .xml ファイルでは省略可能です。 [ **表示** ] コマンドを使用して、SCW の .xml ファイルを表示すると、指定した .xml ファイルの正しい既定の変換が自動的に読み込まれます。 .Xsl 変換が指定されている場合、変換が .xsl トランス フォームと同じディレクトリに .xml ファイルであることを前提として記述する必要があります。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="example"></a>例

*Xsl*変換を使用して*Policyfile.xml*を表示するには、次のように入力します。

```
scwcmd view /x:C:\policies\Policyfile.xml /s:C:\viewers\Policyview.xsl
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [scwcmd analyze コマンド](scwcmd-analyze.md)

- [scwcmd configure コマンド](scwcmd-configure.md)

- [scwcmd register コマンド](scwcmd-register.md)

- [scwcmd rollback コマンド](scwcmd-rollback.md)

- [scwcmd transform コマンド](scwcmd-transform.md)