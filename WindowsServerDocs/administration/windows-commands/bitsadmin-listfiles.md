---
title: bitsadmin listfiles
description: 指定されたジョブ内のファイルを一覧表示する bitsadmin listfiles コマンドの参照記事です。
ms.topic: reference
ms.assetid: ad0d1eaa-3bd8-45e5-8f72-4da7366f0d59
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: b6afadf78acd187b336484db47b128afb49e27fe
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024306"
---
# <a name="bitsadmin-listfiles"></a>bitsadmin listfiles

指定されたジョブ内のファイルを一覧表示します。

## <a name="syntax"></a>構文

```
bitsadmin /listfiles <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのファイルの一覧を取得するには、次のようにします。

```
bitsadmin /listfiles myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
