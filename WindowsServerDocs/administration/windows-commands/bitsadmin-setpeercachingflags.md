---
title: bitsadmin setpeercachingflags
description: Bitsadmin setpeercachingflags コマンドの参照記事。ジョブのファイルをキャッシュしてピアに提供できるかどうか、およびジョブがピアからコンテンツをダウンロードできるかどうかを決定するフラグを設定します。
ms.topic: reference
ms.assetid: 3f54a127-fb68-49a5-b843-664ec833df67
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 1305d8d865f51556f4b518c7972eaff4ca9ec3e5
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026210"
---
# <a name="bitsadmin-setpeercachingflags"></a>bitsadmin setpeercachingflags

ジョブのファイルをキャッシュしてピアに提供できるかどうか、およびジョブがピアからコンテンツをダウンロードできるかどうかを決定するフラグを設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setpeercachingflags <job> <value>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| value | 次を含む符号なし整数。<ul><li>**1.** ジョブは、ピアからコンテンツをダウンロードできます。</li><li>**2.** ジョブのファイルをキャッシュしてピアに配信できます。</li></ul> |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブでピアからコンテンツをダウンロードできるようにするには、次のようにします。

```
bitsadmin /setpeercachingflags myDownloadJob 1
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
