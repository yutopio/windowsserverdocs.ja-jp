---
title: コンテキストの設定
description: Set context コマンドの参照記事。シャドウコピーの作成のコンテキストを設定します。
ms.topic: reference
ms.assetid: fc16c7dd-e8f0-4c2a-8742-0bddb2848bfd
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ce1414ab90f116f58618fcd67bc203f25dc58e46
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389096"
---
# <a name="set-context"></a>コンテキストの設定

シャドウ コピーの作成のコンテキストを設定します。 パラメーターを指定せずに使用する場合 **セット コンテキスト** コマンド プロンプトでヘルプを表示します。

## <a name="syntax"></a>構文

```
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| clientaccessible | シャドウ コピーがクライアントのバージョンの Windows で使用できることを指定します。 既定では、このコンテキストは永続的です。 |
| 一貫 | シャドウ コピーがプログラムの終了、リセット、または再起動の間で永続化することを指定します。 |
| volatile | 上のシャドウ コピーの削除は、終了またはリセットします。 |
| nowriters | すべてのライターを除外することを指定します。 |

## <a name="examples"></a>例

シャドウ コピーが DiskShadow を終了するときに削除されないようにするには、次のように入力します。

```
set context persistent
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [メタデータの設定コマンド](set-metadata.md)

- [set option コマンド](set-option.md)

- [詳細コマンドの設定](set-verbose.md)
