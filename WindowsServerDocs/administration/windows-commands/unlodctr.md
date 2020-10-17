---
title: unlodctr
description: Unlodctr コマンドの参照記事。サービスまたはデバイスドライバーのパフォーマンスカウンター名と説明テキストをシステムレジストリから削除します。
ms.topic: reference
ms.assetid: fc8aa6f0-c1d9-47ea-937a-28152148e774
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3983f98df0de6a8048f78b6ebdb16cccafea8da4
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156693"
---
# <a name="unlodctr"></a>unlodctr

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サービスまたはデバイスドライバーの **パフォーマンスカウンター名** と **説明テキスト** をシステムレジストリから削除します。

> [!WARNING]
> レジストリを正しく編集しないと、システムが正常に動作しなくなる場合があります。 レジストリを変更する前に、コンピューター上の重要なデータのバックアップを作成する必要があります。

## <a name="syntax"></a>構文

```
unlodctr <drivername>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<drivername>` | Windows Server レジストリから、ドライバーまたはサービスの **パフォーマンスカウンターの名前** 設定と **説明テキスト** を削除し `<drivername>` ます。 にスペースが含まれている場合は、 `<drivername>` テキストを引用符で囲む必要があります ("Driver name" など)。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>使用例

簡易メール転送プロトコル (SMTP) サービスの現在の **パフォーマンスカウンターの名前** と **説明テキスト** を削除するには、次のように入力します。

```
unlodctr SMTPSVC
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
