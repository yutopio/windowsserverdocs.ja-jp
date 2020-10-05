---
title: wdsutil set-デバイス
description: Wdsutil set-device の参照記事。事前設定されたコンピューターの属性を変更します。
ms.topic: reference
ms.assetid: 401567f8-eaeb-4a2d-b811-140bb007028d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 9844df011a01419599463a26cc4b78761af7cdbd
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730658"
---
# <a name="wdsutil-set-device"></a>wdsutil set-デバイス

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

事前設定されたコンピューターの属性を変更します。 事前登録されたコンピューターとは、active directory ドメインサーバー (AD DS) のコンピューターアカウントオブジェクトにリンクされているコンピューターのことです。 事前登録されたクライアントは、既知のコンピューターとも呼ばれます。 クライアントのインストールを管理するコンピューター アカウントのプロパティを構成できます。 たとえば、ネットワーク ブート プログラムとクライアントが受信すると、無人セットアップ ファイルだけでなく、クライアントがネットワーク ブート プログラムをダウンロードする必要があります、サーバーを構成できます。

## <a name="syntax"></a>構文
```
wdsutil [Options] /Set-Device /Device:<Device name> [/ID:<UUID | MAC address>] [/ReferralServer:<Server name>] [/BootProgram:<Relative path>]
[/WdsClientUnattend:<Relative path>] [/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relative path>] [/Domain:<Domain>] [/resetAccount]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|ドライブ<computer name>|コンピューター (SAM アカウント名) の名前を指定します。|
|[/Id: < UUID & #124 文字です。MAC アドレス >]|GUID/UUID またはコンピューターの MAC アドレスのいずれかを指定します。 この値は、次の 3 つの形式のいずれかである必要があります。<p>-バイナリ文字列: **/ID:ACEFA3E81F20694E953EB2DAA1E8B1B6**<br />文字列の GUID/UUID:/id:**E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6**<br />MAC アドレス: **00B056882FDC** (ダッシュ) または **00-B0-56-88-2F-DC** (ダッシュ付き)|
|[/ReferralServer:<Server name>]|簡易ファイル転送プロトコル (tftp) を使用してネットワークブートプログラムとブートイメージをダウンロードするために、接続するサーバーの名前を指定します。|
|[/BootProgram:<Relative path>]|RemoteInstall フォルダーから、指定したコンピューターが受信するネットワークブートプログラムへの相対パスを指定します。 例: **boot\x86\ pxeboot.com**|
|[/WdsClientUnattend:<Relative path>]|Windows 展開サービスクライアントのインストール画面を自動化する無人セットアップファイルへの remoteInstall フォルダーからの相対パスを指定します。|
|[/User: <Domain\User &#124; User@Domain>]|指定したユーザー、コンピューターをドメインに参加させるために必要な権限を与えるコンピューター アカウント オブジェクトのアクセス許可を設定します。|
|[/JoinRights: {JoinOnly & #124 文字です。完全}]|ユーザーに割り当てられる権限の種類を指定します。<p>-   **Joinonly** では、ユーザーがコンピューターをドメインに参加させる前に、管理者がコンピューターアカウントをリセットする必要があります。<br />-   **Full** を使用すると、コンピューターをドメインに参加させる権限を含め、ユーザーにフルアクセスできます。|
|[/JoinDomain: {[はい] (& a) #124 文字です。No}]|ドメインに、Windows 展開サービスのインストール中のこのコンピューター アカウントとコンピューターを参加する必要があるかどうかを指定します。 既定の設定は **[はい]** です。|
|[/BootImagepath: <Relative path> ]|コンピューターが使用するブートイメージを remoteInstall フォルダーからの相対パスで指定します。|
|[/ドメイン:<Domain>]|事前登録されたコンピューターを検索するドメインを指定します。 既定値は、ローカル ドメインです。|
|[/resetAccount]|適切なアクセス許可を持つすべてのユーザーがこのアカウントを使用してドメインに参加できるように、指定したコンピューターのアクセス許可をリセットします。|
## <a name="examples"></a>例
コンピューターのネットワーク ブート プログラムと参照サーバーを設定するには、次のように入力します。
```
wdsutil /Set-Device /Device:computer1 /ReferralServer:MyWDSServer
/BootProgram:boot\x86\pxeboot.n12
```
コンピューターのさまざまな設定を指定するには、次のように入力します。
```
wdsutil /verbose /Set-Device /Device:computer2 /ID:00-B0-56-88-2F-DC /WdsClientUnattend:WDSClientUnattend\unattend.xml
/User:Domain\user /JoinRights:JoinOnly /JoinDomain:No /BootImagepath:boot\x86\images\boot.wim /Domain:NorthAmerica /resetAccount
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil デバイスの追加コマンド](wdsutil-add-device.md)
- [wdsutil get-alldevices コマンド](wdsutil-get-alldevices.md)
- [wdsutil get-デバイスコマンド](wdsutil-get-device.md)
