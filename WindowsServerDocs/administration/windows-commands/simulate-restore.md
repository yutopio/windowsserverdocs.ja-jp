---
title: simulate restore
description: 復元前または PostRestore イベントをライターに発行せずに、コンピューター上の復元セッションでライターが関与することをテストするシミュレートされた復元のリファレンス記事です。
ms.topic: reference
ms.assetid: d883d94c-3cb1-4848-9d74-1b4378044b31
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5640f69f421d65588251ff1e15b63cbeaffde613
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89036980"
---
# <a name="simulate-restore"></a>復元をシミュレートします。

発行することがなく、コンピューター上の復元のセッション内のライターをテスト **復元前** または **PostRestore** ライターへのイベントです。

## <a name="syntax"></a>構文

```
simulate restore
```

## <a name="remarks"></a>解説

-   **復元をシミュレート** ライタ搭載の復元を成功させるために動作しているかどうかをテストするために使用します。
-   使用する前に **リストアをシミュレート**, を使用して、DiskShadow メタデータ ファイルを読み込む必要があります、 **メタデータの読み込み** コマンドです。 これには、選択されているライターと復元のコンポーネントが読み込まれます。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)