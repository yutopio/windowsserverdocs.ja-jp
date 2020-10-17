---
title: vssadmin list shadows
description: 指定されたボリュームの既存のシャドウコピーをすべて一覧表示する vssadmin list shadows コマンドの説明です。
ms.topic: reference
author: JasonGerend
ms.author: jgerend
ms.date: 05/18/2018
ms.localizationpriority: medium
ms.openlocfilehash: cb7ddaa09e2da350c1c5422c6224aabd8831f763
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156204"
---
# <a name="vssadmin-list-shadows"></a>vssadmin list shadows

> 適用対象: Windows 10、Windows 8.1、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

指定したボリュームの既存のシャドウコピーをすべて一覧表示します。 パラメーターを指定せずにこのコマンドを使用すると、コンピューター上のすべてのボリュームシャドウコピーが、 **シャドウコピーセット**によって指定された順序で表示されます。

## <a name="syntax"></a>構文

```
vssadmin list shadows [/for=<ForVolumeSpec>] [/shadow=<ShadowID>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /for =`<ForVolumeSpec>` | シャドウコピーが表示されるボリュームを指定します。 |
| /シャドウ =`<ShadowID>` | ShadowID によって指定されたシャドウコピーの一覧を表示します。 シャドウコピー ID を取得するには、 [vssadmin list shadows コマンド](vssadmin-list-shadows.md)を使用します。 シャドウコピー ID を入力するときは、次の形式を使用します。各 *X* は16進文字を表します。<p>XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX-XXXX-XXXX-XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [vssadmin コマンド](vssadmin.md)

- [vssadmin list shadows コマンド](vssadmin-list-shadows.md)
