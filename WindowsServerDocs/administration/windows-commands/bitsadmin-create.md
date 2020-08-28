---
title: bitsadmin create
description: 指定された表示名で転送ジョブを作成する bitsadmin create コマンドの参照記事です。
ms.topic: reference
ms.assetid: 9a8c53af-900b-4c24-9265-5b8b08213fac
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 516f751109724688579f084fd0ccdb5f5bda85a3
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89026680"
---
# <a name="bitsadmin-create"></a>bitsadmin create

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定された表示名を使用して転送ジョブを作成します。

> [!NOTE]
> **/Upload**   および/ **uploadの**パラメーターの型は、BITS 1.2 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /create [type] displayname
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| type | ジョブには次の3つの種類があります。<ul><li>**ダウンロード.** サーバーからローカルファイルにデータを転送します。</li><li>**5d.** ローカルファイルからサーバーにデータを転送します。</li><li>**/Upload-Reply.** ローカルファイルからサーバーにデータを転送し、サーバーから応答ファイルを受信します。</li></ul>このパラメーターの既定値は、指定されていない場合は **/ダウンロード** です。 |
| displayName | 新しく作成されたジョブに割り当てられた表示名。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のダウンロードジョブを作成するには、次のようにします。

```
bitsadmin /create myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin resume コマンド](bitsadmin-resume.md)

- [bitsadmin コマンド](bitsadmin.md)
