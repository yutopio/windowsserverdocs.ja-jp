---
title: subst
description: Subst コマンドの参照記事。パスとドライブ文字を関連付けます。
ms.topic: reference
ms.assetid: 3e69234c-2312-4343-868b-afc1017c622a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 52d45c9139c70c4f513a972f7789f872145c8b63
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718229"
---
# <a name="subst"></a>subst

ドライブ文字をパスに関連付けます。 パラメーターを指定せずに使用する場合 **subst** 仮想ドライブの名前が有効で表示されます。

## <a name="syntax"></a>構文

```
subst [<drive1>: [<drive2>:]<path>]
subst <drive1>: /d
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<drive1>:` | パスに割り当てる仮想ドライブを指定します。 |
| `[<drive2>:]<path>` | 物理ドライブと仮想ドライブに指定するパスを指定します。 |
| /d | 置き換えられた (仮想) ドライブを削除します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="remarks"></a>解説

- 次のコマンドは機能しません。 **subst** コマンドで指定されているドライブでは使用できません。

  - [chkdsk コマンド](chkdsk.md)

    [コマンドの実行](diskcomp.md)

    [diskcopy コマンド](diskcopy.md)

    [format コマンド](format.md)

    [label コマンド](label.md)

    [回復コマンド](recover.md)

- パラメーターは、 `<drive1>` **リソース** コマンドで指定された範囲内である必要があります。 それ以外の場合、 **subst** によって次のエラーメッセージが表示されます。 `Invalid parameter - drive1:`

## <a name="examples"></a>例

パス b:\user\betty\forms の仮想ドライブ z を作成するには、次のように入力します。

```
subst z: b:\user\betty\forms
```

完全なパスを入力する代わりに次のように、コロンで後に仮想ドライブの文字を入力してこのディレクトリに移動することができます。

```
z:
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)