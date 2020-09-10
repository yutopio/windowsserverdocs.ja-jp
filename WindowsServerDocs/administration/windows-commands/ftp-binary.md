---
title: ftp binary
description: Ftp バイナリコマンドの参照記事。ファイル転送の種類を binary に設定します。
ms.topic: reference
ms.assetid: ee925b4d-85d2-47b1-b7d6-3832b7ec5505
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 725dc41eaa8800372b438e85fbb430edcbf04832
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638543"
---
# <a name="ftp-binary"></a>ftp binary

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ファイル転送の種類をバイナリに設定します。 **Ftp**コマンドでは、ASCII (既定) とバイナリイメージファイル転送の両方の種類がサポートされますが、実行可能ファイルを転送する場合はバイナリを使用することをお勧めします。 バイナリモードでは、ファイルは1バイト単位で転送されます。

## <a name="syntax"></a>構文

```
binary
```

### <a name="examples"></a>例

ファイル転送の種類を binary に設定するには、次のように入力します。

```
binary
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ftp ascii コマンド](ftp-ascii.md)

- [追加の FTP ガイダンス](/previous-versions/orphan-topics/ws.10/cc756013(v=ws.10))
