---
title: fsutil wim
description: Windows イメージ (WIM) でサポートされているファイルを検出および管理するための機能を提供する、fsutil wim コマンドのリファレンス記事です。
manager: dmoss
ms.author: toklima
author: toklima
ms.assetid: 6c6ff819-f349-4aea-b0be-1f637f631736
ms.topic: reference
ms.date: 10/16/2017
ms.openlocfilehash: 6e1bb492911250161e1e4a57983ea9c58f3a34ff
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89032870"
---
# <a name="fsutil-wim"></a>fsutil wim

> 適用先:Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows 10

Windows イメージ (WIM) でサポートされているファイルを検出および管理するための機能を提供します。

## <a name="syntax"></a>構文

```
fsutil wim [enumfiles] <drive name> <data source>
fsutil wim [enumwims] <drive name>
fsutil wim [queryfile] <filename>
fsutil wim [removewim] <drive name> <data source>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| enumfiles | WIM によってサポートされるファイルを列挙します。 |
| `<drive name>` | ドライブ名を指定します。 |
| `<data source>` | データソースを指定します。 |
| enumwims | バッキング WIM ファイルを列挙します。 |
| queryfile | ファイルが WIM によってバックアップされているかどうかを照会し、その場合は WIM ファイルの詳細を表示します。 |
| `<filename>` | ファイル名を指定します。 |
| removewim | バッキングファイルから WIM を削除します。 |

### <a name="examples"></a>例

データソース0からドライブ C のファイルを列挙するには、次のように入力します。

```
fsutil wim enumfiles C: 0
```

ドライブ C: のバッキング WIM ファイルを列挙するには、次のように入力します。

```
fsutil wim enumwims C:
```

ファイルが WIM でバックアップされているかどうかを確認するには、次のように入力します。

```
fsutil wim C:\Windows\Notepad.exe
```

ボリューム C: とデータソース2のバッキングファイルから WIM を削除するには、次のように入力します。

```
fsutil wim removewims C: 2
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [fsutil](fsutil.md)
