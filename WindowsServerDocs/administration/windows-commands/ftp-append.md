---
title: ftp append
description: Ftp append コマンドの参照記事。現在のファイルの種類の設定を使用して、リモートコンピューター上のファイルにローカルファイルを追加します。
ms.topic: reference
ms.assetid: 7c1a133c-31dc-41a4-9eb9-258efd79804d
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 58f85a99eed60bffafaa71d9b0af1cc67462453b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037750"
---
# <a name="ftp-append"></a>ftp append

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

現在のファイルの種類の設定を使用して、リモートコンピューター上のファイルにローカルファイルを追加します。

## <a name="syntax"></a>構文

```
append <localfile> [remotefile]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<localfile>` | 追加するローカルファイルを指定します。 |
| remotefile | を追加するリモートコンピューター上のファイルを指定し <localfile> ます。 このパラメーターを使用しない場合は、 `<localfile>` リモートファイル名の代わりに名前が使用されます。 |

### <a name="examples"></a>例

リモートコンピューター上の*file2.txt*に*file1.txt*を追加するには、次のように入力します。

```
append file1.txt file2.txt
```

リモートコンピューター上の*file1.txt*という名前のファイルにローカル*file1.txt*を追加する場合は。

```
append file1.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
