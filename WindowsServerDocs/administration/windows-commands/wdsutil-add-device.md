---
title: wdsutil デバイスの追加
description: Active Directory Domain Services でコンピューターを事前にステージングする、wdsutil add-device コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 1e599cc4-464a-421b-b6bb-c101af154131
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: de05d5510e61f5cba0813a7e11215935fd380968
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524638"
---
# <a name="wdsutil-add-device"></a>wdsutil デバイスの追加

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Active Directory Domain Services (AD DS) でコンピューターを事前にステージングします。 事前にステージングされたコンピューターは、 *既知のコンピューター*とも呼ばれます。 これにより、クライアントのインストールを制御するプロパティを構成できます。 たとえば、ネットワーク ブート プログラムとクライアントが受信すると、無人セットアップ ファイルだけでなく、クライアントがネットワーク ブート プログラムをダウンロードする必要があります、サーバーを構成できます。

## <a name="syntax"></a>構文

```
wdsutil /add-Device /Device:<Devicename> /ID:<UUID | MAC address> [/ReferralServer:<Servername>] [/BootProgram:<Relativepath>] [/WdsClientUnattend:<Relativepath>] [/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/BootImagepath:<Relativepath>] [/OU:<DN of OU>] [/Domain:<Domain>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| ドライブ`<Devicename>` | 追加するデバイスの名前を指定します。 |
| 番号`<UUID|MAC address>` | GUID/UUID またはコンピューターの MAC アドレスのいずれかを指定します。 GUID/UUID は、バイナリ文字列 ( `/ID:ACEFA3E81F20694E953EB2DAA1E8B1B6` ) または guid 文字列 () の2つの形式のいずれかである必要があり `/ID:E8A3EFAC-201F-4E69-953E-B2DAA1E8B1B6` ます。 MAC アドレスは、次の形式である必要があります: **00B056882FDC** (ダッシュ) または **00-B0-56-88-2F-DC** (ダッシュ付き) |
| [/ReferralServer:`<Servername>`] | 簡易ファイル転送プロトコル (tftp) を使用して、ネットワークブートプログラムとブートイメージをダウンロードするために、接続するサーバーの名前を指定します。 |
| [/BootProgram:`<Relativepath>`] | **RemoteInstall**フォルダからこのコンピュータが受信するネットワークブートプログラムへの相対パスを指定します。 例: `boot\x86\pxeboot.com` |
| [/WdsClientUnattend:`<Relativepath>`] | Windows 展開サービスクライアントのインストール画面を自動化する無人インストールファイルへの **remoteInstall** フォルダーからの相対パスを指定します。 |
| [/User: `<Domain\User|User@Domain>` ] | 指定したユーザー、コンピューターをドメインに参加させるために必要な権限を与えるコンピューター アカウント オブジェクトのアクセス許可を設定します。 |
| [/Joinrights: `{JoinOnly|Full}` ] | ユーザーに割り当てられる権限の種類を指定します。<ul><li>**Joinonly** -ユーザーがコンピューターをドメインに参加させる前に、管理者がコンピューターアカウントをリセットする必要があります。</li><li>**Full** -ユーザーにフルアクセス権を付与します。これには、コンピューターをドメインに参加させる権限も含まれます。 |
| [/Joindomain: `{Yes|No}` ] | オペレーティングシステムのインストール中に、コンピューターをこのコンピューターアカウントとしてドメインに参加させるかどうかを指定します。 既定値は **[はい]** です。 |
| [/BootImagepath: `<Relativepath>` ] | このコンピューターで使用するブートイメージを **remoteInstall** フォルダーからの相対パスで指定します。 |
| [/OU:`<DN of OU>`] | コンピューター アカウント オブジェクトを作成する必要が組織単位の識別名。 例: **OU = MyOU, CN テスト, DC = Domain, DC = com を =** です。 既定の場所は、既定のコンピュータのコンテナーです。 |
| [/ドメイン:`<Domain>`] | コンピューター アカウント オブジェクトを作成するドメイン。 既定の場所は、ローカル ドメインです。 |

## <a name="examples"></a>例

コンピューターを追加するには、MAC アドレスを使用して、次のように入力します。

```
wdsutil /add-Device /Device:computer1 /ID:00-B0-56-88-2F-DC
```

コンピューターを追加するには、GUID 文字列を使用して、次のように入力します。

```
wdsutil /add-Device /Device:computer1 /ID:{E8A3EFAC-201F-4E69-953F-B2DAA1E8B1B6} /ReferralServer:WDSServer1 /BootProgram:boot\x86\pxeboot.com/WDSClientUnattend:WDSClientUnattend\unattend.xml /User:Domain\MyUser/JoinRights:Full /BootImagepath:boot\x86\images\boot.wim /OU:OU=MyOU,CN=Test,DC=Domain,DC=com
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil get-alldevices コマンド](wdsutil-get-alldevices.md)

- [wdsutil get-デバイスコマンド](wdsutil-get-device.md)

- [wdsutil set-デバイスコマンド](wdsutil-set-device.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)

- [New-WdsClient](/powershell/module/wds/New-WdsClient)
