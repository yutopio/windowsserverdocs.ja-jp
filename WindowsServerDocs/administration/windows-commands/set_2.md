---
title: set_2
description: シャドウコピーの作成に使用するコンテキスト、オプション、詳細モード、およびメタデータファイルを設定する set_2 の参照記事です。
ms.topic: reference
ms.assetid: acf24663-1a50-4321-b48d-1717655e9476
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 685f66692e324b29bb0a33aaaefaec44b52b218d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639476"
---
# <a name="set_2"></a>set_2

コンテキスト、オプション、詳細出力モード、およびシャドウ コピーの作成のメタデータ ファイルを設定します。 パラメーターを指定せずに使用する場合 **設定** すべて現在の設定を一覧表示します。

## <a name="syntax"></a>Syntax

```
set
set context {clientaccessible | persistent [nowriters] | volatile [nowriters]}
set option {[differential | plex] [transportable] [[rollbackrecover] [txfrecover] | [noautorecover]]}
set verbose {on|off}
set metadata <MetaData.cab>
```

## <a name="set-sub-commands"></a>サブコマンドの設定

|サブコマンド|説明|
|-----------|-----------|
|context|シャドウ コピーの作成のコンテキストを設定します。 参照してください [セット コンテキスト](set-context.md) 構文およびパラメーターについてです。|
|オプション|シャドウ コピーの作成のオプションを設定します。 参照してください [オプション設定](set-option.md) 構文およびパラメーターについてです。|
|verbose|詳細出力モードを有効または無効にします。 参照してください [が詳細設定](set-verbose.md) 構文およびパラメーターについてです。|
|metadata|シャドウの作成のメタデータ ファイルの場所と名前を設定します。 参照してください [メタデータ設定](set-metadata.md) 構文およびパラメーターについてです。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)