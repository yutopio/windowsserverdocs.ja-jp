---
title: Sc.exe の削除
description: sc.exe ユーティリティを使用してサービスの登録を解除する方法について説明します
ms.topic: reference
ms.assetid: 2fe94fb3-e4d1-47b5-b999-39995ecbb644
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 09a3f43824c3e0c895331326341b92c7c6aa5727
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89037540"
---
# <a name="scexe-delete"></a>Sc.exe の削除

レジストリからサービス サブキーを削除します。 サービスが実行されている場合、または別のプロセスにサービスへの開いているハンドルがある場合は、サービスが削除対象としてマークします。

このコマンドを使用する方法の例については、[例](#examples)を参照してください。

## <a name="syntax"></a>構文

```
sc.exe [<ServerName>] delete [<ServiceName>]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|\<ServerName>|サービスが配置されているリモート サーバーの名前を指定します。 名前には、汎用名前付け規則 (UNC) 形式 (myserver など) を使用する必要があり \\ \\ ます。 SC.exe をローカルで実行するには、このパラメーターを省略します。|
|\<ServiceName>|によって返されるサービスの名前を指定、 **られて** 操作します。|
|?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>解説

sc.exe を使用して、DHCP、DNS、インターネットインフォメーションサービスなどの組み込みのオペレーティングシステムサービスを削除することはお勧めしません。 オペレーティングシステムの役割、サービス、およびコンポーネントをインストール、削除、または再構成するには、「[役割、役割サービス、または機能のインストールまたはアンインストール](/WindowsServerDocs/administration/server-manager/install-or-uninstall-roles-role-services-or-features.md)」を参照してください。

## <a name="examples"></a>例

サービス サブキーを削除する **NewServ** 、ローカル コンピューター上のレジストリから入力します。
```
sc.exe delete newserv
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
