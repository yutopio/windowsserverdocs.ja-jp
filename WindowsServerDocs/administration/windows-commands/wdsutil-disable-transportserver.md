---
title: wdsutil サーバーの無効化
description: Wdsutil disable transportserver コマンドの参照記事。トランスポートサーバーのすべてのサービスを無効にします。
ms.topic: reference
ms.assetid: a009706b-8e89-486b-8e3d-512cd9f4de74
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4bbb177897e3a779de275957949b0dcf62e53478
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93070354"
---
# <a name="wdsutil-disable-transportserver"></a>wdsutil サーバーの無効化

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

トランスポート サーバーのすべてのサービスを無効にします。

## <a name="syntax"></a>構文

```
wdsutil [Options] /Disable-TransportServer [/Server:<Servername>]
```

### <a name="parameters"></a>パラメーター

|パラメーター|[説明]|
|-------|--------|
|[/Server:`<Servername>`]|無効にするトランスポート サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 トランスポート サーバーの名前が指定されていない場合は、ローカルのサーバーが使用されます。|

## <a name="examples"></a>例

サーバーを無効にするには、次のいずれかを入力します。

```
wdsutil /Disable-TransportServer
```

```
wdsutil /verbose /Disable-TransportServer /Server:MyWDSServer
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil enable transportserver コマンド](wdsutil-enable-transportserver.md)

- [wdsutil get transportserver コマンド](wdsutil-get-transportserver.md)

- [wdsutil set transportserver コマンド](wdsutil-set-transportserver.md)

- [wdsutil start-transportserver コマンド](wdsutil-start-transportserver.md)

- [wdsutil stop transportserver コマンド](wdsutil-stop-transportserver.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
