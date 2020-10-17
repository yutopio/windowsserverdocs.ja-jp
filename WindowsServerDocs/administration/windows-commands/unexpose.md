---
title: unexpose
description: 公開されているシャドウコピーを公開しないコマンドの参照記事です。
ms.topic: reference
ms.assetid: 58dc7d0f-52e9-4587-9487-d3b4c3e52640
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 35e545d632790f8c4d7d69d6e9fea1e7e1a07dc4
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156311"
---
# <a name="unexpose"></a>unexpose

[ [公開] コマンド](expose.md)を使用して公開されたシャドウコピーを公開しません。 公開されたシャドウコピーは、シャドウ ID、ドライブ文字、共有、またはマウントポイントによって指定できます。

## <a name="syntax"></a>構文

```
unexpose {<shadowID> | <drive:> | <share> | <mountpoint>}
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<shadowID>` | 指定したシャドウ ID によって指定されたシャドウコピーを表示します。 の代わりに、既存のエイリアスまたは環境変数を使用でき `<shadowID>` ます。 既存のすべてのエイリアスを表示するには、パラメーターを指定せずに [add コマンド](add.md) を使用します。 |
| `<drive:>` | 指定したドライブ文字 (ドライブ P など) に関連付けられているシャドウコピーを表示します。 |
| `<share>` | 指定した共有に関連付けられているシャドウコピーを表示します (たとえば、 `\\MachineName` )。 |
| `<mountpoint>` | 指定したマウントポイント (など) に関連付けられているシャドウコピーを表示し `C:\shadowcopy\` ます。 |
| add | パラメーターを指定せずに使用すると、既存のエイリアスが表示されます。 |

## <a name="examples"></a>使用例

* ドライブ P: に関連付けられているシャドウコピーを公開しないようにするには \* 、次のように入力します。

```
unexpose P:
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コマンドの追加](add.md)

- [コマンドの公開](expose.md)
