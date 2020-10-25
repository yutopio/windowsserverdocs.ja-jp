---
title: Update-ServerFiles
description: 更新プログラム ServerFiles のリファレンス記事。サーバーの%Windir%\System32\RemInst フォルダーに格納されている最新のファイルを使用して、REMINST 共有フォルダー内のファイルを更新します。
ms.topic: reference
ms.assetid: 23aa79df-38c6-401e-91bd-cd23811b30b4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7684dfb694ac6814d00c91363d6573be5cf7be7f
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524897"
---
# <a name="update-serverfiles"></a>Update-ServerFiles

サーバーの %Windir%\System32\RemInst フォルダーに格納されている最新のファイルを使用して、REMINST 共有フォルダー内のファイルを更新します。 Windows 展開サービス インストールの有効性を確実には、Windows 展開サービスのファイルに、各サーバーのアップグレード、サービス パックのインストールまたは更新後に 1 回このコマンドを実行する必要があります。

## <a name="syntax"></a>構文

```
wdsutil [Options] /Update-ServerFiles [/Server:<Server name>]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|[/Server:\<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|

## <a name="examples"></a>例

ファイルを更新するには、次のいずれかを入力します。
```
wdsutil /Update-ServerFiles
wdsutil /Verbose /Progress /Update-ServerFiles /Server:MyWDSServer
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)