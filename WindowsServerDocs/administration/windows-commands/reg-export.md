---
title: reg export
description: Reg export コマンドの参照記事。これにより、ローカルコンピューターの指定したサブキー、エントリ、および値が、他のサーバーに転送するためにファイルにコピーされます。
ms.topic: reference
ms.assetid: 0ad9526f-1e29-4fa5-9d2d-feaa92f12d7c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a7bf8abe5dd97463202a024da90523a52020a986
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89627053"
---
# <a name="reg-export"></a>reg export

他のサーバーに転送するためのファイルに指定されたサブキー、エントリ、およびローカル コンピューターの値をコピーします。

## <a name="syntax"></a>構文

```
reg export <keyname> <filename> [/y]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
|--|--|
| `<keyname>` | サブキーの完全なパスを指定します。 エクスポート操作は、ローカルコンピューターでのみ機能します。 *Keyname*には、有効なルートキーを含める必要があります。 ローカルコンピューターの有効なルートキーは、 **HKLM**、 **HKCU**、 **HKCR**、 **HKU**、および **HKCC**です。 レジストリキー名にスペースが含まれている場合は、キー名を引用符で囲みます。 |
| `<filename>` | 操作中に作成されるファイルのパスと名前を指定します。 拡張子が .reg のファイルが必要です。 |
| /y | 確認を求めるメッセージを表示せずに、名前 *filename* を持つ既存のファイルを上書きします。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- **Reg エクスポート**操作の戻り値は次のとおりです。

    | 値 | 説明 |
    |--|--|
    | 0 | 成功 |
    | 1 | 障害 |

### <a name="examples"></a>例

すべてのサブキーの内容は、MyApp キーの値を AppBkUp.reg ファイルをエクスポートするには、次のように入力します。

```
reg export HKLM\Software\MyCo\MyApp AppBkUp.reg
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
