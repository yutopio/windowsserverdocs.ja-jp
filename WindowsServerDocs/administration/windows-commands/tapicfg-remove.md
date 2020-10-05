---
title: tapicfg の削除
description: Tapicfg remove コマンドの参照記事。これにより、TAPI アプリケーションディレクトリパーティションが削除されます。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 09/29/2020
ms.openlocfilehash: 5d5b7e1cc5d362d66041a292e86e022187896dea
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731186"
---
# <a name="tapicfg-remove"></a>tapicfg の削除

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

TAPI アプリケーション ディレクトリ パーティションを削除します。

> [!IMPORTANT]
> このコマンドを実行するには、active directory の Enterprise Admins グループのメンバーである必要があります。

## <a name="syntax"></a>構文

```
tapicfg remove /directory:<partitionname>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `/directory:<partitionname>` を削除します | 必須。 削除するには、TAPI アプリケーション ディレクトリ パーティションの DNS 名を指定します。 この名前は完全修飾ドメイン名である必要があることに注意してください。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>解説

- このコマンド ライン ツールは、ドメインのメンバーである任意のコンピューターで実行できます。

- 適切なフォントおよび言語のサポートがインストールされている場合、国際または Unicode 文字を含む (TAPI アプリケーション ディレクトリ パーティション、サーバー、およびドメインの名前) などのユーザー指定のテキストが正しく表示のみ。

- Windows XP または Windows Server 2003 オペレーティング システムを実行している TAPI クライアントは、ILS サーバーまたは TAPI アプリケーション ディレクトリ パーティションのいずれかを照会できますので、ILS が、特定のアプリケーションをサポートするために必要な場合は、組織でインターネット ロケーター サービス (ILS) サーバーを使用することもできます。

- **Tapicfg**を使用して、サービス接続ポイントを作成または削除することができます。 何らかの理由 (たとえば、格納されているドメインの名前を変更する場合)、TAPI アプリケーション ディレクトリ パーティションの名前を変更する場合は、既存のサービス接続ポイントを削除し、発行される TAPI アプリケーション ディレクトリ パーティションの新しい DNS 名を含む新しいものを作成する必要があります。 それ以外の場合、TAPI クライアントを見つけて、TAPI アプリケーション ディレクトリ パーティションにアクセスできません。 (たとえば、特定の TAPI アプリケーション ディレクトリ パーティションに TAPI データを公開するたくはない) 場合は、メンテナンスやセキュリティのためのサービス接続ポイントを削除することもできます。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [tapicfg インストール](tapicfg-install.md)

- [tapicfg publishscp](tapicfg-publishscp.md)

- [tapicfg removescp](tapicfg-removescp.md)

- [tapicfg ショー](tapicfg-show.md)

- [tapicfg makedefault](tapicfg-makedefault.md)