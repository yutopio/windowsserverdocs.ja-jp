---
title: tcmsetup
description: Tcmsetup コマンドのリファレンス記事では、TAPI クライアントを設定して無効にします。
ms.topic: reference
ms.assetid: 15e0c10f-996f-4301-92e5-943f7ee8212d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 315c13310d8059d5553dff9c780fbdd656867a57
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718069"
---
# <a name="tcmsetup"></a>tcmsetup

設定または、TAPI クライアントを無効にします。 TAPI が正常に機能するには、次のコマンドを実行して、TAPI クライアントで使用されるリモートサーバーを指定する必要があります。

> [!IMPORTANT]
> このコマンドを使用するには、ローカルコンピューターの **Administrators** グループのメンバーであるか、適切な権限が委任されている必要があります。 コンピューターがドメインに参加している場合は、 **Domain Admins** グループのメンバーがこの手順を実行できる可能性があります。 セキュリティの点から、[**別のユーザーとして実行**] を使用してこの手順を実行することを検討してください。

## <a name="syntax"></a>構文

```
tcmsetup [/q] [/x] /c <server1> [<server2> …]
tcmsetup  [/q] /c /d
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /q | メッセージ ボックスが表示されないようにします。 |
| /x | 接続指向のコールバックを使用することに大量のトラフィックのネットワーク パケット損失が多いを指定します。 このパラメーターを省略すると、コネクションレス型コールバックが使用されます。 |
| /c | 必須。 クライアントのセットアップを指定します。 |
| `<server1>` | 必須。 クライアントで使用される TAPI サービス プロバイダーのあるリモート サーバーの名前を指定します。 クライアントはサービス プロバイダーの回線や電話を使用します。 クライアントは、サーバーと同じドメインまたはサーバーを含むドメインと双方向の信頼関係があるドメインにする必要があります。 |
| `<server2>…` | その他のサーバーまたはこのクライアントに利用可能なサーバーを指定します。 サーバーの一覧を指定する場合は、スペースを使用して、サーバー名を区切ります。 |
| /d | リモート サーバーの一覧をクリアします。 リモート サーバー上にある TAPI サービス プロバイダーを使用できなくなり、TAPI クライアントを無効にします。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- クライアント ユーザーは、TAPI サーバー上、電話または回線を使用できるように、テレフォニー サーバーの管理者は、電話または回線にユーザーを割り当てる必要があります。

- このコマンドによって作成されるテレフォニー サーバーの一覧には、クライアントで利用できるテレフォニー サーバーの既存の一覧が置き換えられます。 このコマンドを使用して既存のリストにを追加することはできません。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [コマンド シェルの概要](/previous-versions/windows/it-pro/windows-server-2003/cc737438(v=ws.10))

- [クライアント コンピューター上のテレフォニー サーバーを指定します。](/previous-versions/windows/it-pro/windows-server-2003/cc759226(v=ws.10))

- [回線または電話に対してテレフォニー ユーザーを割り当てる](/previous-versions/windows/it-pro/windows-server-2003/cc736875(v=ws.10))
