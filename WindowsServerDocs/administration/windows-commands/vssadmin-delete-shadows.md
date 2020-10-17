---
title: vssadmin delete shadows
description: 指定されたボリュームのシャドウコピーを削除する vssadmin delete shadows コマンドの説明です。
ms.topic: reference
author: JasonGerend
ms.author: jgerend
ms.date: 05/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: 2dcd1bf8cbe946c77d0b5a100d2a29ecb36ef50f
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156229"
---
# <a name="vssadmin-delete-shadows"></a>vssadmin delete shadows

> 適用対象: Windows 10、Windows 8.1、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

指定されたボリュームのシャドウコピーを削除します。 シャドウコピーを削除できるのは、 *クライアントからアクセス可能* な型の場合のみです。

## <a name="syntax"></a>構文

```
vssadmin delete shadows /for=<ForVolumeSpec> [/oldest | /all | /shadow=<ShadowID>] [/quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /for =`<ForVolumeSpec>` | 削除するボリュームのシャドウコピーを指定します。 |
| /最も古い | 最も古いシャドウコピーだけを削除します。 |
| /all | 指定されたボリュームのシャドウコピーをすべて削除します。 |
| /シャドウ =`<ShadowID>` | ShadowID によって指定されたシャドウコピーを削除します。 シャドウコピー ID を取得するには、 [vssadmin list shadows コマンド](vssadmin-list-shadows.md)を使用します。 シャドウコピー ID を入力するときは、次の形式を使用します。各 *X* は16進文字を表します。<p>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX-XXXX-XXXX-XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX |
| スイッチを | コマンドが実行中にメッセージを表示しないように指定します。 |

## <a name="examples"></a>使用例

ボリューム C の最も古いシャドウコピーを削除するには、次のように入力します。

```
vssadmin delete shadows /for=c: /oldest
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [vssadmin コマンド](vssadmin.md)

- [vssadmin list shadows コマンド](vssadmin-list-shadows.md)
