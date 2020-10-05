---
title: tapicfg
description: この tapicfg コマンドのリファレンス記事では、TAPI アプリケーションディレクトリパーティションを作成、削除、または表示したり、既定の TAPI アプリケーションディレクトリパーティションを設定したりします。
ms.topic: reference
ms.assetid: c0e642ce-5d98-4edb-9a65-1dff09aef4e1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 17b596036251d6ea8588de3b70359ea161b67c58
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718129"
---
# <a name="tapicfg"></a>tapicfg

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

作成、削除、または TAPI アプリケーション ディレクトリ パーティションを表示または既定の TAPI アプリケーション ディレクトリ パーティションを設定します。 TAPI 3.1 クライアントは、このアプリケーションディレクトリパーティションの情報をディレクトリサービスロケーターサービスと共に使用して、TAPI ディレクトリを検索し、通信することができます。 また、 **tapicfg** を使用してサービス接続ポイントを作成または削除することもできます。これにより、tapi クライアントがドメイン内の tapi アプリケーションディレクトリパーティションを効率的に検索できるようになります。

このコマンド ライン ツールは、ドメインのメンバーである任意のコンピューターで実行できます。

## <a name="syntax"></a>構文

```
tapicfg install
tapicfg remove
tapicfg publishscp
tapicfg removescp
tapicfg show
tapicfg makedefault
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| [tapicfg インストール](tapicfg-install.md) | TAPI アプリケーション ディレクトリ パーティションを作成します。 |
| [tapicfg の削除](tapicfg-remove.md) | TAPI アプリケーション ディレクトリ パーティションを削除します。|
| [tapicfg publishscp](tapicfg-publishscp.md) | TAPI アプリケーション ディレクトリ パーティションを公開するサービス接続ポイントを作成します。 |
| [tapicfg removescp](tapicfg-removescp.md) | TAPI アプリケーション ディレクトリ パーティション用のサービス接続ポイントを削除します。 |
| [tapicfg ショー](tapicfg-show.md) | ドメインの名前と TAPI アプリケーション ディレクトリ パーティションの場所が表示されます。 |
| [tapicfg makedefault](tapicfg-makedefault.md) | ドメインの既定の TAPI アプリケーション ディレクトリ パーティションを設定します。 |

#### <a name="remarks"></a>解説

- **Tapicfg インストール**(tapi アプリケーションディレクトリパーティションを作成) または**TAPICFG remove** (tapi アプリケーションディレクトリパーティションを削除するため) のいずれかを実行するには、Active Directory の**Enterprise Admins**グループのメンバーである必要があります。

- 適切なフォントおよび言語のサポートがインストールされている場合、国際または Unicode 文字を含む (TAPI アプリケーション ディレクトリ パーティション、サーバー、およびドメインの名前) などのユーザー指定のテキストが正しく表示のみ。

- Windows XP または Windows Server 2003 オペレーティング システムを実行している TAPI クライアントは、ILS サーバーまたは TAPI アプリケーション ディレクトリ パーティションのいずれかを照会できますので、ILS が、特定のアプリケーションをサポートするために必要な場合は、組織でインターネット ロケーター サービス (ILS) サーバーを使用することもできます。

- **Tapicfg**を使用して、サービス接続ポイントを作成または削除することができます。 何らかの理由 (たとえば、格納されているドメインの名前を変更する場合)、TAPI アプリケーション ディレクトリ パーティションの名前を変更する場合は、既存のサービス接続ポイントを削除し、発行される TAPI アプリケーション ディレクトリ パーティションの新しい DNS 名を含む新しいものを作成する必要があります。 それ以外の場合、TAPI クライアントを見つけて、TAPI アプリケーション ディレクトリ パーティションにアクセスできません。 (たとえば、特定の TAPI アプリケーション ディレクトリ パーティションに TAPI データを公開するたくはない) 場合は、メンテナンスやセキュリティのためのサービス接続ポイントを削除することもできます。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [tapicfg インストール](tapicfg-install.md)

- [tapicfg の削除](tapicfg-remove.md)

- [tapicfg publishscp](tapicfg-publishscp.md)

- [tapicfg removescp](tapicfg-removescp.md)

- [tapicfg ショー](tapicfg-show.md)

- [tapicfg makedefault](tapicfg-makedefault.md)
