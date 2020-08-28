---
title: 'secedit: validate'
description: 参照記事 * * * *-
ms.topic: reference
ms.assetid: 9fb06354-f55a-4ca4-9fbc-9a872eb9b9cf
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 47c0ec78cb49da3ce256e7a74ce8be003b0db85b
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89027980"
---
# <a name="seceditvalidate"></a>secedit: validate



セキュリティ テンプレート (.inf ファイル) に格納されているセキュリティ設定を検証します。

## <a name="syntax"></a>構文

```
Secedit /validate <configuration file name>

```

#### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|[構成ファイル名]|必須。</br>検証で適用するセキュリティ テンプレートのパスとファイル名を指定します。|

## <a name="remarks"></a>解説

セキュリティ テンプレートを検証する場合に役立ちますが破損しているまたは不適切に設定します。

無効なセキュリティ テンプレートは適用されません。

ログ ファイルは更新されません。

Windows Server 2008 で `Secedit /refreshpolicy` に置き換えられました `gpupdate`します。 セキュリティ設定を更新する方法については、次を参照してください。 [Gpupdate](gpupdate.md)します。

## <a name="examples"></a>例

いることを確認するセキュリティ テンプレートに、ロールバックが実行されると、ロールバック inf ファイル、secRBKcontoso.inf は無効です。
```
Secedit /validate secRBKcontoso.inf
```

## <a name="additional-references"></a>その他の参照情報

-   [Secedit:generaterollback](secedit-generaterollback.md)
-   [Secedit](secedit.md)
- [コマンド ライン構文の記号](command-line-syntax-key.md)