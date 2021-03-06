---
title: reg compare
description: 指定されたレジストリサブキーまたはエントリを比較する reg compare コマンドの参照記事。
ms.topic: reference
ms.assetid: 177dc6a3-034e-4846-a394-330d03c14e0b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 51c385b9a051574602c2508b8efd8f657c62ec7c
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627097"
---
# <a name="reg-compare"></a>reg compare

比較では、レジストリ サブキーまたはエントリを指定します。

## <a name="syntax"></a>構文

```
reg compare <keyname1> <keyname2> [{/v Valuename | /ve}] [{/oa | /od | /os | on}] [/s]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<keyname1>` | サブキーまたは追加されるエントリの完全なパスを指定します。 リモートコンピューターを指定するには、コンピューター名 (形式) を `\\<computername>\` *keyname*の一部として含めます。 省略 `\\<computername>\` すると、操作は既定でローカルコンピューターに設定されます。 *Keyname*には、有効なルートキーを含める必要があります。 ローカルコンピューターの有効なルートキーは、 **HKLM**、 **HKCU**、 **HKCR**、 **HKU**、および **HKCC**です。 リモートコンピューターが指定されている場合、有効なルートキーは **HKLM** と **HKU**です。 レジストリキー名にスペースが含まれている場合は、キー名を引用符で囲みます。 |
| `<keyname2>` | 比較する 2 つ目のサブキーの完全なパスを指定します。 リモートコンピューターを指定するには、コンピューター名 (形式) を `\\<computername>\` *keyname*の一部として含めます。 省略 `\\<computername>\` すると、操作は既定でローカルコンピューターに設定されます。 *Keyname2*にコンピューター名のみを指定すると、 *keyname1*で指定されたサブキーへのパスが操作によって使用されます。 *Keyname*には、有効なルートキーを含める必要があります。 ローカルコンピューターの有効なルートキーは、 **HKLM**、 **HKCU**、 **HKCR**、 **HKU**、および **HKCC**です。 リモートコンピューターが指定されている場合、有効なルートキーは **HKLM** と **HKU**です。 レジストリキー名にスペースが含まれている場合は、キー名を引用符で囲みます。 |
| /v `<Valuename>` | サブキーの下を比較する値の名前を指定します。 |
| /ve | Null 値の名前を持つエントリのみを比較することを指定します。 |
| /oa | すべての相違点との一致が表示されることを指定します。 既定では、差分のみが一覧表示します。 |
| /od | 相違点だけが表示されることを指定します。 これは既定の動作です。 |
| /os | 一致だけが表示されることを指定します。 既定では、差分のみが一覧表示します。 |
| /on | 何も表示されないことを指定します。 既定では、差分のみが一覧表示します。 |
| /s | すべてのサブキーとエントリを再帰的を比較します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- **Reg compare**操作の戻り値は次のとおりです。

    | 値 | 説明 |
    |--|--|
    | 0 | 比較の結果が成功して、結果は変わりません。 |
    | 1 | 比較が失敗しました。 |
    | 2 | 比較が成功し、相違が検出されました。 |

- 結果に表示されるシンボルは次のとおりです。

    | シンボル | 説明 |
    |--|--|
    | = | *KeyName1* データに等しい *KeyName2* データ。 |
    | < | *KeyName1* データより小さい *KeyName2* データ。 |
    | > | *KeyName1* データがより大きい *KeyName2* データ。 |

### <a name="examples"></a>例

キー **MyApp** の下にあるすべての値を、キー **Savemyapp**の下のすべての値と比較するには、次のように入力します。

```
reg compare HKLM\Software\MyCo\MyApp HKLM\Software\MyCo\SaveMyApp
```

キー **MyCo** の下のバージョンの値と、 **MyCo1**キーの下のバージョンの値を比較するには、次のように入力します。

```
reg compare HKLM\Software\MyCo HKLM\Software\MyCo1 /v Version
```

HKLM\Software\MyCo の下にあるすべてのサブキーと値を、HKLM\Software\MyCo の下にあるすべてのサブキーと値を使用して、次のように入力します。

```
reg compare \\ZODIAC\HKLM\Software\MyCo \\. /s
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
