---
title: bitsadmin addfileset
description: Bitsadmin addfileset コマンドの参照記事。指定されたジョブに1つ以上のファイルを追加します。
ms.topic: reference
ms.assetid: 75466994-262f-4724-b14d-f813c5397675
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 2b9b93f38f3604c4f0a9fcaf886d74356d355086
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89033710"
---
# <a name="bitsadmin-addfileset"></a>bitsadmin addfileset

指定されたジョブに1つ以上のファイルを追加します。

## <a name="syntax"></a>構文

```
bitsadmin /addfileset <job> <textfile>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| textfile | テキストファイル。各行には、リモートファイル名とローカルファイル名が含まれています。 **注:** 名前はスペースで区切る必要があります。 文字で始まる行 `#` は、コメントとして扱われます。 |

## <a name="examples"></a>例

```
bitsadmin /addfileset files.txt
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
