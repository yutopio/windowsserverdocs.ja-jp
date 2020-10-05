---
title: wdsutil の進行状況
description: コマンドの実行中に進行状況を表示する、wdsutil progress の参照記事。
ms.topic: reference
ms.assetid: 8ce5e77b-e13f-4ac3-948d-31770a6c7e25
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4a7ddc18db35b110c8b5c513f798e3408aafd93f
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730697"
---
# <a name="wdsutil-progress"></a>wdsutil/progress

コマンドの実行中に進行状況を表示します。 実行するその他の wdsutil コマンドでは、 **/progress** を使用できます。 このコマンドの詳細ログ記録を有効にする場合は、 **wdsutil**の後に **/verbose**および **/progress**を直接指定する必要があります。

## <a name="syntax"></a>構文

```
wdsutil /progress <commands>
```

## <a name="examples"></a>例

サーバーを初期化して進行状況を表示、次のように入力します。

```
wdsutil /verbose /progress /Initialize-Server /Server:MyWDSServer /RemInst:C:\RemoteInstall
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)