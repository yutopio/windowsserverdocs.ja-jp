---
title: sxstrace
description: Systrace コマンドのリファレンス記事。サイドバイサイドの問題を診断するのに役立ちます。
ms.topic: reference
ms.assetid: fcd26eeb-fbd9-4a86-b6a9-dfa5e9c6e4fc
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 95f52993db56e61b3a1cd4d26a0ef36626421a15
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718209"
---
# <a name="sxstrace"></a>sxstrace

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サイド バイ サイドの問題を診断します。

## <a name="syntax"></a>構文

```
sxstrace [{[trace -logfile:<filename> [-nostop]|[parse -logfile:<filename> -outfile:<parsedfile>  [-filter:<appname>]}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| trace | のトレースをサイドバイサイドで有効にします。 |
| -logfile | 未処理のログ ファイルを指定します。 |
| `<filename>` | トレースログをに保存 `<filename` します。 |
| -nostop | トレースを停止するためのプロンプトが表示されないことを指定します。 |
| parse | 生のトレース ファイルに変換します。 |
| -出力 | 出力ファイル名を指定します。 |
| `<parsedfile>` | 解析されたファイルのファイル名を指定します。 |
| -filter | フィルター選択される出力を使用します。 |
| `<appname>` | アプリケーションの名前を指定します。 |
| stoptrace | トレースが停止されていない場合は、停止します。 |
| -? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

トレースを有効にし、トレースファイルを *sxstrace*に保存するには、次のように入力します。

```
sxstrace trace -logfile:sxstrace.etl
```

生のトレースファイルを人間が判読できる形式に変換し、結果を *sxstrace.txt*に保存するには、次のように入力します。

```
sxstrace parse -logfile:sxstrace.etl -outfile:sxstrace.txt
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
