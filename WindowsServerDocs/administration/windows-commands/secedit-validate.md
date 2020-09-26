---
title: secedit validate
description: セキュリティテンプレートに格納されているセキュリティ設定を検証する、secedit validate コマンドの参照記事。
ms.topic: reference
ms.assetid: 9fb06354-f55a-4ca4-9fbc-9a872eb9b9cf
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 057573cf5bc28a47f5140fb58e23ee1ed4bbc4c1
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388103"
---
# <a name="secedit-validate"></a>secedit/validate

セキュリティ テンプレート (.inf ファイル) に格納されているセキュリティ設定を検証します。 セキュリティテンプレートを検証すると、破損しているか、不適切に設定されているかを判断するのに役立ちます。 セキュリティテンプレートが破損しているか、不適切に設定されています。

## <a name="syntax"></a>構文

```
secedit /validate <configuration file name>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| `<configuration file name>` | 必須です。 検証で適用するセキュリティ テンプレートのパスとファイル名を指定します。 このコマンドでは、ログファイルは更新されません。 |

## <a name="examples"></a>例

ロールバック後も、ロールバック .inf ファイル " *Secrbkcontoso .inf*" が引き続き有効であることを確認するには、次のように入力します。

```
secedit /validate secRBKcontoso.inf
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [secedit/analyze](secedit-analyze.md)

- [secedit/configure](secedit-configure.md)

- [secedit/export](secedit-export.md)

- [secedit/generaterollback](secedit-generaterollback.md)

- [secedit/import](secedit-import.md)