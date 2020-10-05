---
title: wdsutil remove-namespace
description: Wdsutil remove-namespace のリファレンス記事。カスタム名前空間が削除されます。
ms.topic: reference
ms.assetid: 4eb758b6-8519-4e26-9fe0-2e19bb0e8702
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: bc5d44b727bf93bf6630f7289833640397e69dae
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731276"
---
# <a name="wdsutil-remove-namespace"></a>wdsutil remove-namespace

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

カスタムの名前空間を削除します。

## <a name="syntax"></a>構文
```
wdsutil /remove-Namespace /Namespace:<Namespace name> [/Server:<Server name>] [/force]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|空間<Namespace name>|名前空間の名前を指定します。 フレンドリ名ではありませんし、一意である必要があります。<p>-   **展開サーバーの役割サービス**: 名前空間名の構文は/NAMESPACE: WDS: <ImageGroup> / <ImageName> / <Index> です。 例: **WDS:ImageGroup1/install.wim/1**<br />-   **トランスポートサーバーの役割サービス**: この値は、サーバー上で作成されたときに名前空間に指定された名前と一致する必要があります。|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。|
|/force|名前空間を直ちに削除し、すべてのクライアントを終了します。 **/Force**を指定しない限り、既存のクライアントは転送を完了できますが、新しいクライアントは参加できません。|
## <a name="examples"></a>例
名前空間を停止する (現在のクライアントは、転送を完了できますが、新しいクライアントが参加することができません、) の種類。
```
wdsutil /remove-Namespace /Namespace:Custom Auto 1
```
すべてのクライアントの終了時に、次のように入力します。
```
wdsutil /remove-Namespace /Server:MyWDSServer /Namespace:Custom Auto 1 /force
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil get-allnamespaces コマンド](wdsutil-get-allnamespaces.md)
- [wdsutil new-namespace コマンド](wdsutil-new-namespace.md)
- [wdsutil start-namespace コマンド](wdsutil-start-namespace.md)
