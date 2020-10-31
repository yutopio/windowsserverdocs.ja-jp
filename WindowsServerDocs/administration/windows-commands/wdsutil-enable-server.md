---
title: wdsutil enable-サーバー
description: Wdsutil enable server コマンドのリファレンス記事。 Windows 展開サービスのすべてのサービスを有効にします。
ms.topic: reference
ms.assetid: 939ffbfb-cf3c-4310-9627-6e7e0c0644d6
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2e2f62198ce4c012245174bc00e536e15ecd1c27
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93070324"
---
# <a name="wdsutil-enable-server"></a>wdsutil enable-サーバー

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Windows 展開サービスのすべてのサービスを有効にします。

## <a name="syntax"></a>構文

```
wdsutil [options] /Enable-Server [/Server:<Servername>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |

## <a name="examples"></a>例

サーバーでサービスを有効にするには、次のいずれかを入力します。

```
wdsutil /Enable-Server
```

```
wdsutil /verbose /Enable-Server /Server:MyWDSServer
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil disable-サーバーコマンド](wdsutil-disable-server.md)

- [wdsutil get サーバーコマンド](wdsutil-get-server.md)

- [wdsutil initialize-サーバーコマンド](wdsutil-initialize-server.md)

- [wdsutil set-サーバーコマンド](wdsutil-set-server.md)

- [wdsutil start-サーバーコマンド](wdsutil-start-server.md)

- [wdsutil stop-サーバーコマンド](wdsutil-stop-server.md)

- [wdsutil 初期化解除-サーバーコマンド](wdsutil-uninitialize-server.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
