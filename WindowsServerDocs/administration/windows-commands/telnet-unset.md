---
title: telnet unset
description: 以前に設定したオプションをオフにする telnet 設定の参照記事。
ms.topic: reference
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 8e6e15e3f4b5a74c77f4a184c6641d0c14a18662
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038299"
---
# <a name="telnet-unset"></a>telnet: 未設定

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

以前の set オプションをオフにします。

## <a name="syntax"></a>構文
```
u[nset] {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]
```
#### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|bsasdel|送信 **Backspace** として、 **Backspace**します。|
|crlf|送信、 **Enter** CR としてキー。 呼ばれるモードを改行します。|
|delasbs|Delete **を** **delete**として送信します。|
|エスケープ|エスケープ文字の設定を削除します。|
|localecho|Localecho オフにします。|
|ログ|ログ記録をオフにします。|
|ntlm|NTLM 認証をオフにします。|
|?|このコマンドのヘルプを表示します。|
## <a name="examples"></a>例
ログをオフにします。
```
u logging
```
## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)
