---
title: wdsutil get alldevices
description: Wdsutil get alldevices コマンドのリファレンス記事。事前にステージングされたすべてのコンピューターの Windows 展開サービスプロパティを表示します。
ms.topic: reference
ms.assetid: 5824b3d2-2df1-4ed6-a289-e6c47c13fea2
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a960a30fd61056e2e2eb183e8a873223daa78be2
ms.sourcegitcommit: 28b5ab74cb0b40539ccc1a83998d6391e87fe51f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96614874"
---
# <a name="wdsutil-get-alldevices"></a>wdsutil get alldevices

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

事前にステージングされたすべてのコンピューターの Windows 展開サービスプロパティを表示します。 事前にステージングされたコンピューターとは、active directory ドメインサービスのコンピューターアカウントにリンクされている物理コンピューターのことです。

## <a name="syntax"></a>構文

```
wdsutil [options] /get-alldevices [/forest:{Yes | No}] [/referralserver:<servername>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `[/forest:{Yes | No}]` | Windows 展開サービスがフォレスト全体またはローカル ドメインでコンピューターを返すかどうかを指定します。 既定の設定は **いいえ**, 、ローカル ドメイン内のコンピューターのみが返されることを意味します。 |
| `[/referralserver:<servername>]` | 指定されたサーバーに事前にステージングされているコンピューターのみを返します。 |

## <a name="examples"></a>例

すべてのコンピューターを表示するには、次のいずれかを入力します。

```
wdsutil /get-alldevices
```

```
wdsutil /verbose /get-alldevices /forest:Yes /referralserver:MyWDSServer
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil set-デバイスコマンド](wdsutil-set-device.md)

- [wdsutil デバイスの追加コマンド](wdsutil-add-device.md)

- [wdsutil get-デバイスコマンド](wdsutil-get-device.md)
