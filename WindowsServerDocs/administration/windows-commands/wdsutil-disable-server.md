---
title: wdsutil サーバーの無効化
description: Wdsutil disable server コマンドのリファレンス記事。 Windows 展開サービスサーバーのすべてのサービスを無効にします。
ms.topic: reference
ms.assetid: b69fcfe0-b744-4794-bc75-2c9218c0ba66
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: d8af0a0c929e2bff341b2b5bff71d0838b09d418
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93070394"
---
# <a name="wdsutil-disable-server"></a>wdsutil サーバーの無効化

Windows 展開サービス サーバーのすべてのサービスを無効にします。

## <a name="syntax"></a>構文

```
wdsutil [Options] /Disable-Server [/Server:<Server name>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。 |

## <a name="examples"></a>例

サーバーを無効にするには、次のいずれかを入力します。

```
wdsutil /Disable-Server
```

```
wdsutil /Verbose /Disable-Server /Server:MyWDSServer
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
