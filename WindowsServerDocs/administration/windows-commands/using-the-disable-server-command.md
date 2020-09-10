---
title: サーバーを無効にする
description: Windows 展開サービスサーバーのすべてのサービスを無効にする無効化サーバーのリファレンス記事です。
ms.topic: reference
ms.assetid: b69fcfe0-b744-4794-bc75-2c9218c0ba66
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ed8fafb9c35f54656ab4551876dc0461ea1a2c55
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89622035"
---
# <a name="disable-server"></a>サーバーを無効にする

Windows 展開サービス サーバーのすべてのサービスを無効にします。

## <a name="syntax"></a>構文

```
WDSUTIL [Options] /Disable-Server [/Server:<Server name>]
```

### <a name="parameters"></a>パラメーター

|パラメーター|Description|
|---------|-----------|
|[/Server:\<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|

## <a name="examples"></a>例

サーバーを無効にするには、次のいずれかを実行します。
```
WDSUTIL /Disable-Server
WDSUTIL /Verbose /Disable-Server /Server:MyWDSServer
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

