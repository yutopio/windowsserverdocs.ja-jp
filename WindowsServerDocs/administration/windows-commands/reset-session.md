---
title: reset session
description: Reset session コマンドの参照記事。リモートデスクトップセッションホストサーバー上のセッションをリセットできます。
ms.topic: reference
ms.assetid: 4f029ecc-874e-415a-95a8-8b731bae35f9
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 07/11/2018
ms.openlocfilehash: a154ffb27ac8ead093c0e41f9a50d0952b736abc
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037030"
---
# <a name="reset-session"></a>reset session

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートデスクトップセッションホストサーバー上のセッションをリセット (削除) できます。 セッションをリセットする必要がありますのみが正しく動作しないか、または場合に、応答を停止しています。

> [!NOTE]
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
reset session {<sessionname> | <sessionID>} [/server:<servername>] [/v]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<sessionname>` | リセットするセッションの名前を指定します。 セッションの名前を確認するには、 [query session コマンド](query-session.md)を使用します。 |
| `<sessionID>` | リセットするセッションの ID を指定します。 |
| /server:`<servername>` | リセットするセッションに含まれる、ターミナル サーバーを指定します。 それ以外の場合は、現在のリモートデスクトップセッションホストサーバーを使用します。 このパラメーターは、リモートサーバーからこのコマンドを使用する場合にのみ必要です。 |
| /v | 実行されているアクションに関する情報を表示します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

### <a name="remarks"></a>解説

- いつでも独自のセッションをリセットできますが、別のユーザーのセッションをリセットするには、 **フルコントロール** アクセス許可が必要です。 セッションでデータが失われると、ユーザーに警告せずにユーザーのセッションをリセットすることができますを注意してください。

## <a name="examples"></a>例

指定した *rdp tcp # 6*セッションをリセットするには、次のように入力します。

```
reset session rdp-tcp#6
```

*セッション ID 3*を使用するセッションをリセットするには、次のように入力します。

```
reset session 3
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [リモートデスクトップサービスコマンドリファレンス](remote-desktop-services-terminal-services-command-reference.md)
