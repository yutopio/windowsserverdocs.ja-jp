---
title: telnet
description: Telnet サーバーサービスを実行しているコンピューターと通信する telnet コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: b70a6156-9413-4300-84ce-a34c467e2b4e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: cf4fa5754aec18662800f4536afd16a427ca0952
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91717929"
---
# <a name="telnet"></a>telnet

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Telnet サーバーサービスを実行しているコンピューターと通信します。 パラメーターを指定せずにこのコマンドを実行すると、telnet プロンプト (**Microsoft telnet>**) で示されているように、telnet コンテキストを入力できるようになります。 Telnet プロンプトから telnet コマンドを使用して、telnet クライアントを実行しているコンピューターを管理できます。

> [!IMPORTANT]
> このコマンドを実行する前に、telnet クライアントソフトウェアをインストールする必要があります。 詳細については、「 [telnet のインストール](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754293(v=ws.10))」を参照してください。

## <a name="syntax"></a>構文

```
telnet [/a] [/e <escapechar>] [/f <filename>] [/l <username>] [/t {vt100 | vt52 | ansi | vtnt}] [<host> [<port>]] [/?]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /a | 自動ログオンを試行します。 **/L**オプションと同じですが、現在ログオンしているユーザーの名前が使用される点が異なります。 |
| /e `<escapechar>` | Telnet クライアントプロンプトを入力するために使用するエスケープ文字を指定します。 |
| /f `<filename>` | クライアント側のログ記録に使用するファイル名を指定します。 |
| /l `<username>` | リモート コンピューター上でログオンするユーザー名を指定します。 |
| /t `{vt100 | vt52 | ansi | vtnt}` | 端末の種類を指定します。 サポートされているターミナルの種類は、 **vt100**、 **vt52**、 **ansi**、および **vtnt**です。 |
| `<host> [<port>]` | ホスト名またはリモートのコンピューターに、接続して、必要に応じて使用する TCP ポートの IP アドレスを指定します (既定では TCP ポート 23)。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

Telnet を使用して、 *telnet.microsoft.com*で Telnet サーバーサービスを実行しているコンピューターに接続するには、次のように入力します。

```
telnet telnet.microsoft.com
```

Telnet を使用して、 *TCP ポート44の telnet.microsoft.com* で Telnet サーバーサービスを実行しているコンピューターに接続し、ro ログを *telnetlog.txt*という名前のローカルファイルに出力するには、次のように入力します。

```
telnet /f telnetlog.txt telnet.microsoft.com 44
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [Telnet をインストールする](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754293(v=ws.10))

- [telnet のテクニカルリファレンス](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754987(v=ws.10))
