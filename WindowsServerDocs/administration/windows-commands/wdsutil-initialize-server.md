---
title: wdsutil initialize-サーバー
description: Wdsutil initialize-server のリファレンス記事。サーバーの役割がインストールされた後に、Windows 展開サービスサーバーを初期使用するように構成します。
ms.topic: reference
ms.assetid: 68a26ad9-5eb2-4490-b782-b7cd46b8000d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: c61da4f608e825a7cb19c8fb80f8f4b3a5c26fed
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524277"
---
# <a name="wdsutil-initialize-server"></a>wdsutil initialize-サーバー

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

サーバーの役割をインストールした後は、初期使用のための Windows 展開サービス サーバーを構成します。 このコマンドを実行した後、 [wdsutil add-Image コマンド](wdsutil-add-image.md) を使用して、サーバーにイメージを追加する必要があります。
## <a name="syntax"></a>構文
```
wdsutil /Initialize-Server [/Server:<Server name>] /remInst:<Full path> [/Authorize]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|[/Server:<Server name>]|サーバーの名前を指定します。 NetBIOS 名または完全修飾ドメイン名 (FQDN) のいずれかを指定できます。 サーバー名が指定されていない場合は、ローカルのサーバーが使用されます。|
|remInst<Full path>|RemoteInstall フォルダーの完全なパスと名前を指定します。 指定したフォルダーが既に存在しない場合、コマンドの実行時に、このオプションを作成します。 常に発生した場合でも、リモート コンピューターのローカル パスを入力する必要があります。 例: **D:\remoteInstall**。|
|[]、[承認]|動的ホスト制御プロトコル (DHCP) で、サーバーが認証されます。 このオプションは、DHCP 承認されていない検出が有効になっている場合にのみ意味を Windows 展開サービス PXE サーバーで承認する必要 DHCP クライアント コンピューターが処理される前に必要があります。 既定では DHCP 承認されていない検出が無効になっていることに注意してください。|
## <a name="examples"></a>例
サーバーを初期化し、remoteInstall 共有フォルダーを F: ドライブに設定するには、「」と入力します。
```
wdsutil /Initialize-Server /remInst:F:\remoteInstall
```
サーバーを初期化し、remoteInstall 共有フォルダーを C: ドライブに設定するには、「」と入力します。
```
wdsutil /verbose /Progress /Initialize-Server /Server:MyWDSServer /remInst:C:\remoteInstall
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil disable-サーバーコマンド](wdsutil-disable-server.md)
- [wdsutil enable-サーバーコマンド](wdsutil-enable-server.md)
- [wdsutil get サーバーコマンド](wdsutil-get-server.md)
- [wdsutil set-サーバーコマンド](wdsutil-set-server.md)
- [wdsutil start-サーバーコマンド](wdsutil-start-server.md)
- [wdsutil stop-サーバーコマンド](wdsutil-stop-server.md)
- [wdsutil 初期化解除-サーバーコマンド](wdsutil-uninitialize-server.md)
