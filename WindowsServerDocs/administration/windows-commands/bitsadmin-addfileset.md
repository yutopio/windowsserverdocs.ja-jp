---
title: bitsadmin addfileset
description: Bitsadmin addfileset コマンドの参照記事。指定されたジョブに1つ以上のファイルを追加します。
ms.topic: reference
ms.assetid: 75466994-262f-4724-b14d-f813c5397675
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2e3e736fe6dcc96b7f81b3b249257f0d23dd78c9
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632715"
---
# <a name="bitsadmin-addfileset"></a>bitsadmin addfileset

指定されたジョブに1つ以上のファイルを追加します。

## <a name="syntax"></a>構文

```
bitsadmin /addfileset <job> <textfile>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
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
