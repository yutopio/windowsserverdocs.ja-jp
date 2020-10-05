---
title: telnet set
description: オプションを設定する telnet set コマンドの参照記事です。
ms.topic: reference
ms.assetid: 67316b5f-9c6f-43e3-86d5-dcff9ae2ac3e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 05678eaa3c4308f72ef4a754cc3e352826fa473a
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91717979"
---
# <a name="telnet-set"></a>telnet: 設定

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

オプションを設定します。 Telnet の設定解除 [コマンド](telnet-unset.md) を使用して、以前に設定されたオプションを無効にすることができます。

## <a name="syntax"></a>構文

```
set [bsasdel] [crlf] [delasbs] [escape <char>] [localecho] [logfile <filename>] [logging] [mode {console | stream}] [ntlm] [term {ansi | vt100 | vt52 | vtnt}] [?]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| bsasdel | **Backspace**を**削除**として送信します。 |
| crlf | CR、LF、(&) を送信 (0x0D、0x0a) と、 **Enter** キーが押されました。 改行 **モード**として知られています。 |
| delasbs | **Delete**を**backspace**として送信します。 |
| 付ける `<character>` | Telnet クライアントプロンプトを入力するために使用するエスケープ文字を設定します。 エスケープ文字、一文字でもかまいませんの組み合わせを使用して、 **ctrl キーを押し** さらに、文字キーです。 コントロール キーの組み合わせを設定するキーを押し、 **CTRL** を割り当てる必要がある文字を入力するときにキーします。 |
| localecho | ローカル エコーをオンにします。 |
| ログファイル `<filename>` | 現在の telnet セッションをローカルファイルに記録します。 ログ記録は、このオプションを設定すると自動的に開始します。 |
| logging | ログ記録を有効にします。 ログ ファイルが設定されていない場合、エラー メッセージが表示されます。 |
| mode `{console | stream}` | 操作モードを設定します。 |
| ntlm | NTLM 認証を有効にします。 |
| 句 `{ansi | vt100 | vt52 | vtnt}` | 端末の種類を設定します。 |
| ? | このコマンドのヘルプを表示します。 |

#### <a name="remarks"></a>解説

- 英語以外のバージョンの telnet では、 **コードセット**を `<option>` 使用できます。 **コードセット** `<option>` 現在のコードセットをオプションに設定します。これには、次のいずれかを指定できます: **SHIFT JIS**、 **日本語 EUC**、 **jis 漢字**、 **Jis 漢字 (78)**、 **DEC 漢字**、 **NEC 漢字**。 同じコードがリモート コンピューターのセットを設定する必要があります。

## <a name="example"></a>例

ログファイルを設定し、ローカルファイル *tnlog.txt*へのログ記録を開始するには、次のように入力します。

```
set logfile tnlog.txt
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
