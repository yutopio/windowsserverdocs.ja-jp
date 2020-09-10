---
title: reg copy
description: レジストリエントリをローカルコンピューターまたはリモートコンピューター上の指定された場所にコピーする reg copy コマンドの参照記事です。
ms.topic: reference
ms.assetid: 3fe74213-39ec-4b2d-ba3d-086243eac997
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7788130e942fb912ac4cf940df48d0bc54a1903b
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627086"
---
# <a name="reg-copy"></a>reg copy

ローカルまたはリモート コンピューター上の指定の場所にレジストリ エントリをコピーします。

## <a name="syntax"></a>構文

```
reg copy <keyname1> <keyname2> [/s] [/f]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
|--|--|
| `<keyname1>` | サブキーまたは追加されるエントリの完全なパスを指定します。 リモートコンピューターを指定するには、コンピューター名 (形式) を `\\<computername>\` *keyname*の一部として含めます。 省略 `\\<computername>\` すると、操作は既定でローカルコンピューターに設定されます。 *Keyname*には、有効なルートキーを含める必要があります。 ローカルコンピューターの有効なルートキーは、 **HKLM**、 **HKCU**、 **HKCR**、 **HKU**、および **HKCC**です。 リモートコンピューターが指定されている場合、有効なルートキーは **HKLM** と **HKU**です。 レジストリキー名にスペースが含まれている場合は、キー名を引用符で囲みます。 |
| `<keyname2>` | 比較する 2 つ目のサブキーの完全なパスを指定します。 リモートコンピューターを指定するには、コンピューター名 (形式) を `\\<computername>\` *keyname*の一部として含めます。 省略 `\\<computername>\` すると、操作は既定でローカルコンピューターに設定されます。 *Keyname*には、有効なルートキーを含める必要があります。 ローカルコンピューターの有効なルートキーは、 **HKLM**、 **HKCU**、 **HKCR**、 **HKU**、および **HKCC**です。 リモートコンピューターが指定されている場合、有効なルートキーは **HKLM** と **HKU**です。 レジストリキー名にスペースが含まれている場合は、キー名を引用符で囲みます。 |
| /s | すべてのサブキーと、指定したサブキーの下にエントリをコピーします。 |
| /f | 確認を求めずに、サブキーをコピーします。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- このコマンドは、サブキーのコピー時に確認を求めません。

- **Reg compare**操作の戻り値は次のとおりです。

    | 値 | 説明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 障害 |

### <a name="examples"></a>例

すべてのサブキーと MyApp のキーの下の値をキー SaveMyApp にコピーするには、次のように入力します。

```
reg copy HKLM\Software\MyCo\MyApp HKLM\Software\MyCo\SaveMyApp /s
```

MyCo MyCo1、現在のコンピューター上のキーに干支をという名前のコンピューター上のキーの下にあるすべての値をコピーするには、次のように入力します。

```
reg copy \\ZODIAC\HKLM\Software\MyCo HKLM\Software\MyCo1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
