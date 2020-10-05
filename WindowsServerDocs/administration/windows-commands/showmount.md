---
title: showmount
description: 指定したコンピューター上の NFS サーバーによってエクスポートされたマウント済みのファイルシステムに関する情報を表示する、showmount-コマンドの参照記事です。
ms.topic: reference
ms.assetid: a6dd562e-e3bd-4ee6-be3b-6d29e29fd20e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 3af87ba4ed42789cf07a2ae63ce9e720043a196e
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91718329"
---
# <a name="showmount"></a>showmount

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

**Showmount-** を使用すると、指定したコンピューター上の NFS サーバーによってエクスポートされたマウント済みのファイルシステムに関する情報を表示できます。 サーバーを指定しない場合、このコマンドは **showmount-** コマンドが実行されているコンピューターに関する情報を表示します。

## <a name="syntax"></a>構文

```
showmount {-e|-a|-d} <server>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -E | サーバーにエクスポートされたすべてのファイルシステムを表示します。 |
| -a | すべてのネットワークファイルシステム (NFS) クライアントと、サーバー上にマウントされているディレクトリを表示します。 |
| -d | NFS クライアントによって現在マウントされているサーバー上のすべてのディレクトリを表示します。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [サービスがネットワーク ファイル システム コマンドのリファレンス](services-for-network-file-system-command-reference.md)