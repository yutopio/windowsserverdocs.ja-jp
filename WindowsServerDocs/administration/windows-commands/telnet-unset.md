---
title: telnet unset
description: Telnet 設定解除コマンドの参照記事。これにより、以前に設定されたオプションはオフになります。
ms.topic: reference
ms.assetid: da9a0d99-1930-4858-93c7-0e9c3797ee09
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 51604615e989325b2e5719d02c51f70dfd84bd0c
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91717919"
---
# <a name="telnet-unset"></a>telnet: 未設定

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

以前の set オプションをオフにします。

## <a name="syntax"></a>構文

```
u {bsasdel | crlf | delasbs | escape | localecho | logging | ntlm} [?]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| bsasdel | Backspace を**backspace**と**して送信**します。 |
| crlf | 送信、 **Enter** CR としてキー。 呼ばれるモードを改行します。 |
| delasbs | Delete **を** **delete**として送信します。 |
| エスケープ | エスケープ文字の設定を削除します。 |
| localecho | Localecho オフにします。 |
| logging | ログ記録をオフにします。 |
| ntlm | NTLM 認証をオフにします。 |
| ? | このコマンドのヘルプを表示します。 |

## <a name="example"></a>例

ログをオフにします。

```
u logging
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
