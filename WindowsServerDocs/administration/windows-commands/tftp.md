---
title: tftp
description: リモートコンピューターとの間でファイルを転送する tftp コマンドの参照記事です。
ms.topic: reference
ms.assetid: 772f19a8-dafe-45cd-878a-f5691f6568ef
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 89a4edb69753ae34814d13f90f21332c6f748244
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91717909"
---
# <a name="tftp"></a>tftp

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

は、簡易ファイル転送プロトコル (tftp) サービスまたはデーモンを実行しているリモートコンピューター (通常は UNIX を実行しているコンピューター) との間でファイルを転送します。 tftp は通常、tftp サーバーからのブートプロセス中にファームウェア、構成情報、またはシステムイメージを取得する組み込みデバイスまたはシステムによって使用されます。

> :Tftp プロトコルでは認証または暗号化メカニズムがサポートされていないため、セキュリティ上のリスクが生じる可能性があります。 インターネットに接続されているシステムには、tftp クライアントをインストールすることはお勧めしません。 Tftp サーバーサービスは、セキュリティ上の理由からマイクロソフトによって提供されなくなりました。

## <a name="syntax"></a>構文

```
tftp [-i] [<host>] [{get | put}] <source> [<destination>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -i | バイナリ イメージの転送モード (オクテット モードとも呼ばれます) を指定します。 画像のバイナリ モードでファイルが 1 バイト単位で転送します。 バイナリ ファイルを転送するときに、このモードを使用します。 **-I**オプションを使用しない場合、ファイルは ASCII モードで転送されます。 これは、既定の転送モードです。 このモードは、行の終わり (EOL) 文字を指定したコンピューターの適切な形式に変換します。 テキスト ファイルを転送するときに、このモードを使用します。 ファイル転送が成功した場合は、データ転送率が表示されます。 |
| `<host>` | ローカルまたはリモート コンピューターを指定します。 |
| get | リモートコンピューター上のファイルの転送 *先* を、ローカルコンピューター上のファイル *ソース* に転送します。 |
| put | ローカルコンピューター上のファイル *ソース* を、リモートコンピューター上のファイル *転送先* に転送します。 Tftp プロトコルではユーザー認証がサポートされていないため、ユーザーはリモートコンピューターにログオンする必要があり、ファイルはリモートコンピューター上で書き込み可能である必要があります。 |
| `<source>` | 転送するファイルを指定します。 |
| `<destination>` | ファイルを転送する場所を指定します。 |

## <a name="examples"></a>例

リモートコンピューターからファイルの *boot.ini* *をコピー*するには、次のように入力します。

```
tftp  -i Host1 get boot.img
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
