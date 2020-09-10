---
title: showmount
description: マウントされたディレクトリを表示する showmount のリファレンス記事です。
ms.topic: reference
ms.assetid: a6dd562e-e3bd-4ee6-be3b-6d29e29fd20e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: e0a03c7e08c80e4cf0b99bbcb74aeff1deccdb1e
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640959"
---
# <a name="showmount"></a>showmount

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

**Showmount-** を使用して、マウントされたディレクトリを表示できます。

## <a name="syntax"></a>構文
```
showmount {-e|-a|-d} <Server>
```

## <a name="description"></a>説明
**Showmount-** コマンド \- ラインユーティリティは、*サーバー*によって指定されたコンピューター上の NFS サーバーによってエクスポートされたマウントされたファイルシステムに関する情報を表示します。 *サーバー*が指定されていない場合、 **showmount-** コマンドを実行し**たコンピューター**に関する情報が表示されます。

次のいずれかのオプションを指定する必要があります。

- ** \- e** -サーバーにエクスポートされたすべてのファイルシステムを表示します。
- ** \- a** -すべてのネットワークファイルシステム \( NFS \) クライアントと、サーバー上の各ディレクトリがマウントされているディレクトリを表示します。
- ** \- d** -NFS クライアントによって現在マウントされているサーバー上のすべてのディレクトリを表示します。

## <a name="see-also"></a>参照
[サービスがネットワーク ファイル システム コマンドのリファレンス](services-for-network-file-system-command-reference.md)