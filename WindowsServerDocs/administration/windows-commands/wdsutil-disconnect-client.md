---
title: wdsutil 切断-クライアント
description: クライアントをマルチキャスト転送または名前空間から切断する、wdsutil disconnect クライアントコマンドの参照記事。
ms.topic: reference
ms.assetid: 876bbe6c-76ab-4de5-879b-d2066e700326
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: dd837fd9a677f78b5890cd1f2092529d44a2bc68
ms.sourcegitcommit: b115e5edc545571b6ff4f42082cc3ed965815ea4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2020
ms.locfileid: "93070334"
---
# <a name="wdsutil-disconnect-client"></a>wdsutil 切断-クライアント

マルチキャスト転送または名前空間を使用して、クライアントを切断します。 **/Force** を指定しない限り、クライアントは別の転送方法 (クライアントでサポートされている場合) にフォールバックします。

## <a name="syntax"></a>構文

```
wdsutil /Disconnect-Client /ClientId:<Client ID> [/Server:<Server name>] [/Force]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| ClientId`<ClientID>` | 切断するようにクライアントの ID を指定します。 クライアントの ID を表示するには、コマンドを実行し `wdsutil /get-multicasttransmission /show:clients` ます。 |
| [/Server:`<Servername>`] | サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| [/Force] | インストールを完全に停止し、フォールバック方式を使用しません。 Wdsmcast.exe はフォールバックメカニズムをサポートしていないため、既定の動作は次のようになります。<ul><li>**Windows 展開サービスクライアントを使用している場合:** クライアントは、ユニキャストを使用してインストールを続行します。</li><li>**Windows 展開サービスクライアントを使用していない場合は、次のようになります。** インストールは失敗します。</li></ul>**重要:** インストールが失敗した場合、コンピューターを使用できない状態にしておくと、このパラメーターを慎重に使用することを強くお勧めします。 |

## <a name="examples"></a>例

クライアントを切断するには、次のように入力します。

```
wdsutil /Disconnect-Client /ClientId:1
```

クライアントを切断し、強制的にインストールが失敗する、次のように入力します。

```
wdsutil /Disconnect-Client /Server:MyWDSServer /ClientId:1 /Force
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil/get-multicasttransmission コマンド](wdsutil-get-multicasttransmission.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
