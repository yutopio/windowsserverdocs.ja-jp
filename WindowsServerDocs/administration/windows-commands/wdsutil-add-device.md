---
title: wdsutil デバイスの追加
description: Active directory ドメインサービスでコンピューターを事前にステージングする、wdsutil 追加デバイスのリファレンス記事です。 プレステージしたコンピューターは、既知のコンピューターとも呼ばれます。
ms.topic: reference
ms.assetid: 1e599cc4-464a-421b-b6bb-c101af154131
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7d87b34028f841340eeaf294a18784c757467b29
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91731126"
---
# <a name="wdsutil-add-device"></a>wdsutil デバイスの追加

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Active directory ドメインサービスでコンピューターを事前にステージングします。 プレステージしたコンピューターは、既知のコンピューターとも呼ばれます。 これにより、クライアントのインストールを制御するプロパティを構成できます。 たとえば、ネットワーク ブート プログラムとクライアントが受信すると、無人セットアップ ファイルだけでなく、クライアントがネットワーク ブート プログラムをダウンロードする必要があります、サーバーを構成できます。

## <a name="syntax"></a>構文
```
wdsutil /add-Device /Device:<Device name> /ID:<UUID | MAC address> [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>]
[/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relative path>] [/OU:<DN of OU>] [/Domain:<Domain>]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|ドライブ<computer name>|追加するコンピューターの名前を指定します。|
|/ID: <UUID &#124; MAC アドレス>|GUID/UUID またはコンピューターの MAC アドレスのいずれかを指定します。 GUID/UUID は、バイナリ文字列または GUID 文字列の2つの形式のいずれかである必要があります。 次に例を示します。<p>バイナリ文字列: **/ID:ACEFA3E81F20694E953EB2DAA1E8B1B6**<p>GUID 文字列: **/ID:E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6**<p>MAC アドレスは、次の形式である必要があります: **00B056882FDC** (ダッシュ) または **00-B0-56-88-2F-DC** (ダッシュ付き)|
|[/ReferralServer:<Server name>]|簡易ファイル転送プロトコル (tftp) を使用して、ネットワークブートプログラムとブートイメージをダウンロードするために、接続するサーバーの名前を指定します。|
|[/BootProgram:<Relative path>]|RemoteInstall フォルダからこのコンピュータが受信するネットワークブートプログラムへの相対パスを指定します。 例: boot\x86\ pxeboot.com|
|[/WdsClientUnattend:<Relative path>]|Windows 展開サービスクライアントのインストール画面を自動化する無人インストールファイルへの remoteInstall フォルダーからの相対パスを指定します。|
|[/User: <Domain\User &#124; User@Domain>]|指定したユーザー、コンピューターをドメインに参加させるために必要な権限を与えるコンピューター アカウント オブジェクトのアクセス許可を設定します。|
|[/JoinRights: {JoinOnly & #124 文字です。完全}]|ユーザーに割り当てられる権限の種類を指定します。<p>-   **Joinonly** では、ユーザーがコンピューターをドメインに参加させる前に、管理者がコンピューターアカウントをリセットする必要があります。<br />-   **Full** を指定すると、コンピューターをドメインに参加させる権限を含む、ユーザーにフルアクセスできます。|
|[/JoinDomain: {[はい] (& a) #124 文字です。No}]|ドメインに、オペレーティング システムのインストール中のこのコンピューター アカウントとコンピューターを参加する必要があるかどうかを指定します。 既定値は **[はい]** です。|
|[/BootImagepath: <Relative path> ]|このコンピューターで使用するブートイメージを remoteInstall フォルダーからの相対パスで指定します。|
|[/OU:<DN of OU>]|コンピューター アカウント オブジェクトを作成する必要が組織単位の識別名。 例: **OU = MyOU, CN テスト, DC = Domain, DC = com を =** です。 既定の場所は、既定のコンピュータのコンテナーです。|
|[/ドメイン:<Domain>]|コンピューター アカウント オブジェクトを作成するドメイン。 既定の場所は、ローカル ドメインです。|
## <a name="examples"></a>例
コンピューターを追加するには、MAC アドレスを使用して、次のように入力します。
```
wdsutil /add-Device /Device:computer1 /ID:00-B0-56-88-2F-DC
```
コンピューターを追加するには、GUID 文字列を使用して、次のように入力します。
```
wdsutil /add-Device /Device:computer1 /ID:{E8A3EFAC-201F-4E69-953F-B2DAA1E8B1B6} /ReferralServer:WDSServer1 /BootProgram:boot\x86\pxeboot.com
/WDSClientUnattend:WDSClientUnattend\unattend.xml /User:Domain\MyUser/JoinRights:Full /BootImagepath:boot\x86\images\boot.wim /OU:OU=MyOU,CN=Test,DC=Domain,DC=com
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil get-alldevices コマンド](wdsutil-get-alldevices.md)
- [wdsutil get-デバイスコマンド](wdsutil-get-device.md)
- [wdsutil set-デバイスコマンド](wdsutil-set-device.md)
- [New-WdsClient](/previous-versions/windows/powershell-scripting/dn283430(v=wps.630))
