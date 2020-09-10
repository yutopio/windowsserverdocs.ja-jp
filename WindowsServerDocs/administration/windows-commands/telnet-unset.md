---
title: telnet unset
description: 以前に設定したオプションをオフにする telnet 設定の参照記事。
ms.topic: reference
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 96b8126d758d5277129f88f193cfea4b25e80584
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640821"
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
|logging|ログ記録をオフにします。|
|ntlm|NTLM 認証をオフにします。|
|?|このコマンドのヘルプを表示します。|
## <a name="examples"></a>例
ログをオフにします。
```
u logging
```
## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)
