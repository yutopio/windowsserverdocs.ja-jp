---
title: Disconnect-Client
description: マルチキャスト転送または名前空間からクライアントを切断する、クライアントの切断に関するリファレンス記事です。
ms.topic: reference
ms.assetid: 876bbe6c-76ab-4de5-879b-d2066e700326
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: cc0d9b21ee7f7a400e363d978ba77778db4eb38a
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524457"
---
# <a name="disconnect-client"></a>Disconnect-Client

マルチキャスト転送または名前空間を使用して、クライアントを切断します。 指定しない限り **/force**, 、クライアントがフォールバックして別の転送方法 (クライアントがサポートされている) 場合。

## <a name="syntax"></a>構文

```
wdsutil /Disconnect-Client /ClientId:<Client ID> [/Server:<Server name>] [/Force]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|ClientId\<Client ID>|切断するようにクライアントの ID を指定します。 クライアントの ID を表示するには、「 **wdsutil/get-multicasttransmission/show: clients**」と入力します。|
|[/Server:\<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。|
|[/Force]|インストールを完全に停止し、フォールバック方式を使用しません。 Wdsmcast.exe が任意のフォールバック メカニズムをサポートしていないことに注意してください。 このオプションを使用しない場合、既定の動作は次に示します。</br>-Windows 展開サービス クライアントを使用している場合、クライアントは、ユニキャストを使用してインストールを続行します。</br>-Windows 展開サービス クライアントを使用していない場合、インストールは失敗します。</br>重要: 、インストールは失敗し、コンピューターを使用できない状態のままでしたので、慎重にこのオプションを使用する必要があります。|

## <a name="examples"></a>例

クライアントを切断するには、次のように入力します。
```
wdsutil /Disconnect-Client /ClientId:1
```
クライアントを切断し、強制的にインストールが失敗する、次のように入力します。
```
wdsutil /Disconnect-Client /Server:MyWDSServer /ClientId:1 /Force
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)