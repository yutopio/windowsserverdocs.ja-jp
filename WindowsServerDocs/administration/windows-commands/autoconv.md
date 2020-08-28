---
title: autoconv
description: ファイルアロケーションテーブル (Fat) および Fat32 ボリュームを NTFS ファイルシステムに変換する autoconv コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 17281e54-0b18-4e84-94ac-24586c82df4e
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 3d69d70200b4885404486bc4956903a17b329630
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89028940"
---
# <a name="autoconv"></a>autoconv

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ファイルアロケーションテーブル (Fat) および Fat32 ボリュームを NTFS ファイルシステムに変換します。これにより、 **autochk** が実行された後も、既存のファイルやディレクトリはそのまま残ります。 NTFS ファイルシステムに変換されたボリュームは、Fat または Fat32 に変換することはできません。

> [!IMPORTANT]
> コマンドラインから **autoconv** を実行することはできません。 **convert.exe**によって設定した場合は、起動時にのみ実行できます。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [autochk コマンド](autochk.md)

- [convert コマンド](convert.md)
