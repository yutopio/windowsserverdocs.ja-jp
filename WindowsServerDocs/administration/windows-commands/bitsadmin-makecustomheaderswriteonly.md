---
title: bitsadmin makecustomheaderswriteonly
description: Bitsadmin makecustomheaderswriteonly コマンドの参照記事です。これにより、ジョブのカスタム HTTP ヘッダーが書き込み専用になります。
ms.topic: reference
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 03/01/2019
ms.openlocfilehash: 4d31f51c2531079342e223752c626b0b7e8d19f8
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89024266"
---
# <a name="bitsadmin-makecustomheaderswriteonly"></a>bitsadmin makecustomheaderswriteonly

ジョブのカスタム HTTP ヘッダーを書き込み専用にします。

> [!IMPORTANT]
> この削除操作は元に戻すことができません。

## <a name="syntax"></a>構文

```
bitsadmin /makecustomheaderswriteonly <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブに対して、カスタム HTTP ヘッダーを書き込み専用にするには、次のようにします。

```
bitsadmin /makecustomheaderswriteonly myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
