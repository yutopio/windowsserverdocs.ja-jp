---
title: wdsutil enable transportserver
description: Wdsutil enable transportserver コマンドのリファレンス記事。これにより、トランスポートサーバーのすべてのサービスが有効になります。
ms.topic: reference
ms.assetid: 9d79dba1-4b57-4a00-8cba-877e6b8618e6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b698a9fae2d730a78497fffe52dc91a68175f0f3
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93070304"
---
# <a name="wdsutil-enable-transportserver"></a>wdsutil enable transportserver

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

トランスポート サーバーのすべてのサービスを有効にします。

## <a name="syntax"></a>構文

```
wdsutil [options] /Enable-TransportServer [/Server:<Servername>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |

## <a name="examples"></a>例

サーバーでサービスを有効にするには、次のいずれかを入力します。

```
wdsutil /Enable-TransportServer
```

```
wdsutil /verbose /Enable-TransportServer /Server:MyWDSServer
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil disable-transportserver コマンド](wdsutil-disable-transportserver.md)

- [wdsutil get transportserver コマンド](wdsutil-get-transportserver.md)

- [wdsutil set transportserver コマンド](wdsutil-set-transportserver.md)

- [wdsutil start-transportserver コマンド](wdsutil-start-transportserver.md)

- [wdsutil stop transportserver コマンド](wdsutil-stop-transportserver.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
