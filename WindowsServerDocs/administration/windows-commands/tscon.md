---
title: tscon
description: リモートデスクトップセッションホストサーバー上の別のセッションに接続する tscon のリファレンス記事です。
ms.topic: reference
ms.assetid: 315a9793-cd10-4987-bb68-89a9d13f7fce
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 17b18aea265ff7c703c2ef6c9c3d0021a9d9ea00
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156394"
---
# <a name="tscon"></a>tscon

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

リモートデスクトップセッションホストサーバー上の別のセッションに接続します。

> [!IMPORTANT]
> 別のセッションに接続するには、 **フルコントロールアクセス** 許可を持っているか、 **特殊なアクセス** 許可を接続している必要があります。

> [!NOTE]
> 最新バージョンの新機能については、「 [Windows Server でのリモートデスクトップサービスの新](/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283323(v=ws.11))機能」を参照してください。

## <a name="syntax"></a>構文

```
tscon {<sessionID> | <sessionname>} [/dest:<sessionname>] [/password:<pw> | /password:*] [/v]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<sessionID>` | 接続先のセッションの ID を指定します。 省略可能なパラメーターを使用する場合は、 `/dest:<sessionname>` 現在のセッションの名前を指定することもできます。 |
| `<sessionname>` | 接続先のセッションの名前を指定します。 |
| /dest`<sessionname>` | 現在のセッションの名前を指定します。 新しいセッションに接続すると、このセッションは切断されます。 また、このパラメーターを使用して、別のユーザーのセッションを別のセッションに接続することもできます。 |
| /password`<pw>` | 接続先のセッションを所有するユーザーのパスワードを指定します。 このパスワードは、接続しているユーザーがセッションを所有していない場合に必要です。 |
| /password`*` | 接続先のセッションを所有するユーザーのパスワードの入力を求めます。 |
| /v | 実行されているアクションに関する情報を表示します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- **/Password**パラメーターでパスワードを指定せず、ターゲットセッションが現在のセッション以外のユーザーに属している場合、このコマンドは失敗します。

- コンソールセッションに接続することはできません。

## <a name="examples"></a>使用例

現在のリモートデスクトップサービスセッションホストサーバーの *セッション 12* に接続し、現在のセッションを切断するには、次のように入力します。

```
tscon 12
```

現在のリモートデスクトップサービスセッションホストサーバーで、パスワード*mypass*使用して*セッション 23*に接続し、現在のセッションを切断するには、次のように入力します。

```
tscon 23 /password:mypass
```

*TERM03*という名前のセッションを*TERM05*という名前のセッションに接続し、セッション*TERM05*を切断するには、次のように入力します。

```
tscon TERM03 /v /dest:TERM05
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [リモート デスクトップ サービス (ターミナル サービス) のコマンド リファレンス](remote-desktop-services-terminal-services-command-reference.md)
