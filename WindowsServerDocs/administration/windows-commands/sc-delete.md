---
title: sc.exe の削除
description: sc.exe delete コマンドのリファレンス記事。レジストリからサービスサブキーを削除します。
ms.topic: reference
ms.assetid: 2fe94fb3-e4d1-47b5-b999-39995ecbb644
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 12c09bd72259a8e4b58f134ca19f1fc825f2f1bb
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388463"
---
# <a name="scexe-delete"></a>sc.exe の削除

レジストリからサービス サブキーを削除します。 サービスが実行されている場合、または別のプロセスにサービスへの開いているハンドルがある場合は、サービスが削除対象としてマークします。

> [!NOTE]
> このコマンドを使用して、DHCP、DNS、インターネットインフォメーションサービスなどの組み込みのオペレーティングシステムサービスを削除することはお勧めしません。 オペレーティングシステムの役割、サービス、およびコンポーネントをインストール、削除、または再構成するには、「[役割、役割サービス、または機能のインストールまたはアンインストール](/WindowsServerDocs/administration/server-manager/install-or-uninstall-roles-role-services-or-features.md)」を参照してください。

## <a name="syntax"></a>構文

```
sc.exe [<servername>] delete [<servicename>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| `<servername>` | サービスが配置されているリモート サーバーの名前を指定します。 名前には、汎用名前付け規則 (UNC) 形式 (myserver など) を使用する必要があり \\ ます。 SC.exe をローカルで実行するには、このパラメーターを使用しないでください。 |
| `<servicename>` | によって返されるサービスの名前を指定、 **られて** 操作します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

サービス サブキーを削除する **NewServ** 、ローカル コンピューター上のレジストリから入力します。

```
sc.exe delete NewServ
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
