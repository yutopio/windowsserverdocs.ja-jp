---
title: tsdiscon
description: Tsdiscon のリファレンス記事。リモートデスクトップセッションホストサーバーからセッションを切断します。
ms.topic: reference
ms.assetid: 13139674-7dee-4965-8cac-32f4928e8b9a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 8b7126e2e9d1f5185ea64566843c523bf0570891
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156386"
---
# <a name="tsdiscon"></a>tsdiscon

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

セッションをリモートデスクトップセッションホストサーバーから切断します。 セッション ID またはセッション名を指定しない場合、このコマンドは現在のセッションを切断します。

> [!IMPORTANT]
> 別のユーザーをセッションから切断するには、 **フルコントロールアクセス** 許可を持っているか、 **特殊なアクセス** 許可を切断する必要があります。

> [!NOTE]
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
tsdiscon [<sessionID> | <sessionname>] [/server:<servername>] [/v]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<sessionID>` | 切断するセッションの ID を指定します。 |
| `<sessionname>` | 切断するセッションの名前を指定します。 |
| /server:`<servername>` | 切断するセッションを含むターミナルサーバーを指定します。 それ以外の場合は、現在のリモートデスクトップセッションホストサーバーが使用されます。 このパラメーターは、リモートサーバーから **tsdiscon** コマンドを実行する場合にのみ必要です。 |
| /v | 実行されているアクションに関する情報を表示します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- セッションを切断したときに実行されているすべてのアプリケーションは、データを失うことなくそのセッションに再接続すると、自動的に実行されます。 [ [セッションのリセット] コマンド](reset-session.md) を使用して、切断されたセッションの実行中のアプリケーションを終了することができますが、これにより、セッションでデータが失われる可能性があります。

- コンソールセッションを切断することはできません。

## <a name="examples"></a>使用例

現在のセッションを切断するには、次のように入力します。

```
tsdiscon
```

*セッション 10*を切断するには、次のように入力します。

```
tsdiscon 10
```

*TERM04*という名前のセッションを切断するには、次のように入力します。

```
tsdiscon TERM04
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)

- [セッションのリセットコマンド](reset-session.md)
