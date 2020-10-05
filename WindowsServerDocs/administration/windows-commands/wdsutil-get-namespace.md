---
title: wdsutil get-名前空間
description: Wdsutil get 名前空間の参照記事。カスタム名前空間に関する情報が表示されます。
ms.topic: reference
ms.assetid: ea641bab-e97b-4909-918e-447730027dc1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2c88bd26af900950c33b059822c08f5afb40de77
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730785"
---
# <a name="wdsutil-get-namespace"></a>wdsutil get-名前空間

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

カスタムの名前空間についての情報を表示します。

## <a name="syntax"></a>構文
Windows Server 2008 R2
```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/Show:Clients]
```
Windows Server 2008 R2
```
wdsutil /Get-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/details:Clients]
```
### <a name="parameters"></a>パラメーター

|               パラメーター               |                                                                                                                                                                                         説明                                                                                                                                                                                          |
|---------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      空間<Namespace name>      | 名前空間の名前を指定します。 これは、フレンドリ名ではない、一意である必要があることに注意してください。<p>-展開サーバー: 名前空間名の構文は、/namspace: WDS: <ImageGroup> / <ImageName> / <Index> です。 例: **WDS:ImageGroup1/install.wim/1**<br />-トランスポート サーバー: この値は、サーバー上で作成されたときに、名前空間に付けた名前と一致する必要があります。 |
|        [/Server:<Server name>]        |                                                                                                             サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。                                                                                                              |
| [/Show: クライアント] または [詳細: クライアント] |                                                                                                                                                  指定した名前空間に接続されているクライアント コンピューターに関する情報を表示します。                                                                                                                                                  |

## <a name="examples"></a>例
名前空間に関する情報を表示するには、次のように入力します。
```
wdsutil /Get-Namespace /Namespace:Custom Auto 1
```
名前空間と接続されているクライアントに関する情報を表示するには、次のいずれかを入力します。
- Windows Server 2008: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /Show:Clients`
- Windows Server 2008 R2: `wdsutil /Get-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /details:Clients`

## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil get-allnamespaces コマンド](wdsutil-get-allnamespaces.md)
- [wdsutil new-namespace コマンド](wdsutil-new-namespace.md)
- [wdsutil remove-namespace コマンド](wdsutil-remove-namespace.md)
- [wdsutil start-namespace コマンド](wdsutil-start-namespace.md)
