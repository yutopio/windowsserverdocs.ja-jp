---
title: manage-bde ステータス
description: BitLocker で保護されているかどうかに関係なく、コンピューター上のすべてのドライブに関する情報を提供する manage-bde status コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 1444a360-fabf-4dd3-b67f-188e6ea3fa5b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ad22cf542aaf3f61d9fe861d20ad25087adfe0a1
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639286"
---
# <a name="manage-bde-status"></a>manage-bde ステータス

コンピューター上のすべてのドライブに関する情報を提供します。BitLocker で保護されているかどうかを示します。次のようなものがあります。

- サイズ

- BitLocker のバージョン

- 変換の状態

- 暗号化された割合

- 暗号化方法

- 保護の状態

- ロックの状態

- 識別フィールド

- キープロテクター

## <a name="syntax"></a>構文

```
manage-bde -status [<drive>] [-protectionaserrorlevel] [-computername <name>] [{-?|/?}] [{-help|-h}]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `<drive>` | コロンの後にドライブ文字を表します。 |
| -protectionaserrorlevel | ボリュームが保護されている場合は、manage-bde コマンドラインツールによってリターンコード **0** が送信され、ボリュームが保護されていない場合は **1** になります。ドライブが BitLocker で保護されているかどうかを判断するためにバッチスクリプトで最もよく使用されます。 使用することも **-p** としてこのコマンドの簡易版です。 |
| -computername | manage-bde.exe が別のコンピューターの BitLocker 保護を変更するために使用されることを指定します。 また、このコマンドの省略版として **-cn** を使用することもできます。 |
| `<name>` | BitLocker による保護を変更するコンピューターの名前を表します。 指定できる値には、コンピューターの NetBIOS 名とコンピューターの IP アドレスが含まれます。 |
| -? または /? | コマンドプロンプトで簡単なヘルプを表示します。 |
| -help または-h | 表示は、コマンド プロンプトでヘルプを完了します。 |

### <a name="examples"></a>例

C ドライブの状態を表示するには、次のように入力します。

```
manage-bde –status C:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [manage-bde コマンド](manage-bde.md)
