---
title: wdsutil allmulticasttransmissions
description: サーバー上のすべてのマルチキャスト転送に関する情報を表示する wdsutil allmulticasttransmissions のリファレンス記事です。
ms.topic: reference
ms.assetid: 95b8fb79-7a8a-4f0c-88f4-92bc1111c67f
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 39405952aac938a7d02ff0f4d1d0c3593df88326
ms.sourcegitcommit: 28b5ab74cb0b40539ccc1a83998d6391e87fe51f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96614854"
---
# <a name="wdsutil-get-allmulticasttransmissions"></a>wdsutil allmulticasttransmissions

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバー上のすべてのマルチキャスト転送に関する情報を表示します。

## <a name="syntax"></a>構文
Windows Server 2008 の場合:
```
wdsutil /Get-AllMulticastTransmissions [/Server:<Server name>] [/Show:Clients] [/ExcludedeletePending]
```
Windows Server 2008 R2 の場合:
```
wdsutil /Get-AllMulticastTransmissions [/Server:<Server name>] [/Show:{Boot | Install | All}] [/details:Clients]  [/ExcludedeletePending]
```
### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| [/Server:<Server name>] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。 |
| [/Show] | **Windows Server 2008**<p>/Show:Clients - マルチキャスト転送に接続されているクライアント コンピューターに関する情報を表示します。<p>**Windows Server 2008 R2**<p>表示: {ブートと #124 文字です。インストールと #124 文字です。すべて} - 返すイメージの種類。                                **ブート** ブート イメージの転送のみを返します。                                  **インストール** インストールのイメージ転送のみを返します。 **すべて** 両方のイメージの種類を返します。 |
|  |  |
| 詳細: クライアント | Windows Server 2008 R2 のみサポートされます。 存在する場合、送信に接続されているクライアントが表示されます。 |
| [/Excludedeletepending] | 一覧から任意の非アクティブ化された転送を除外します。 |

## <a name="examples"></a>例
すべての転送に関する情報を表示するには、次のように入力します。
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Show:All` 表示するには非アクティブ化の転送を除くすべての転送に関する情報を入力します。
- Windows Server 2008: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:Clients /ExcludedeletePending`
- Windows Server 2008 R2: `wdsutil /Get-AllMulticastTransmissions /Server:MyWDSServer /Show:All /details:Clients /ExcludedeletePending`

## <a name="additional-references"></a>その他の参照情報
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-get-multicasttransmission.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-new-multicasttransmission.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-remove-multicasttransmission.md)
- [wdsutil/get-multicasttransmission コマンド](wdsutil-start-multicasttransmission.md)
