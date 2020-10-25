---
title: wdsutil 承認-autoadddevices
description: 管理者の承認が保留中のコンピューターを承認する、wdsutil approval-autoadddevices コマンドの参照記事。
ms.topic: reference
ms.assetid: 8d76e8d3-ab35-429c-be7b-904f95d0782d
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 31dba6d0a0bb585f61433f86d1aa0ae4388fe484
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524937"
---
# <a name="wdsutil-approve-autoadddevices"></a>wdsutil 承認-autoadddevices

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

管理者の承認が保留中のコンピューターを承認します。 自動追加ポリシーを有効にすると、不明なコンピューター (事前に準備されていないコンピューター) がイメージをインストールする前に、管理者の承認が必要になります。 このポリシーを有効にするには、[サーバーのプロパティ] ページの [ **PXE 応答** ] タブを使用します。

## <a name="syntax"></a>構文

```
wdsutil [Options] /Approve-AutoaddDevices [/Server:<Server name>] /RequestId:{<Request ID>| ALL} [/MachineName:<Device name>] [/OU:<DN of OU>] [/User:<Domain\User | User@Domain>] [/JoinRights:{JoinOnly | Full}] [/JoinDomain:{Yes | No}] [/ReferralServer:<Server name>] [/BootProgram:<Relative path>] [/WdsClientUnattend:<Relative path>] [/BootImagepath:<Relative path>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| Server`<Servername>` | サーバーの名前を指定します。 これには、NetBIOS 名または FQDN を指定できます。 サーバー名が指定されていない場合は、ローカル サーバーが使用されます。 |
| RequestId`{Request ID|ALL}` | 保留中のコンピューターに割り当てられた要求 ID を指定します。 指定 **すべて** 保留中のすべてのコンピューターを承認します。 |
| Machinename`<Devicename>` | 追加するデバイスの名前を指定します。 すべてのコンピューターを承認するときに、このオプションを使用することはできません。 |
| [/OU:`<DN of OU>`] | コンピューター アカウント オブジェクトを作成する必要が組織単位の識別名。 例: **OU = MyOU, CN テスト, DC = Domain, DC = com を =** です。 既定の場所は、既定のコンピュータのコンテナーです。 |
| [/User: `<Domain\User|User@Domain>` ] | 指定したユーザー、コンピューターをドメインに参加させるために必要な権限を与えるコンピューター アカウント オブジェクトのアクセス許可を設定します。 |
| [/Joinrights: `{JoinOnly|Full}` ] | ユーザーに割り当てられる権限の種類を指定します。<ul><li>**Joinonly** -ユーザーがコンピューターをドメインに参加させる前に、管理者がコンピューターアカウントをリセットする必要があります。</li><li>**Full** -ユーザーにフルアクセス権を付与します。これには、コンピューターをドメインに参加させる権限も含まれます。 |
| [/Joindomain: `{Yes|No}` ] | オペレーティングシステムのインストール中に、コンピューターをこのコンピューターアカウントとしてドメインに参加させるかどうかを指定します。 既定値は **[はい]** です。 |
| [/ReferralServer:`<Servername>`] | 簡易ファイル転送プロトコル (tftp) を使用して、ネットワークブートプログラムとブートイメージをダウンロードするために接続するサーバーの名前を指定します。 |
| [/BootProgram:`<Relativepath>`] | **RemoteInstall**フォルダからこのコンピュータが受信するネットワークブートプログラムへの相対パスを指定します。 例: **boot\x86\pxeboot.com**します。 |
| [/WdsClientUnattend:`<Relativepath>`] | Windows 展開サービスクライアントを自動化する無人セットアップファイルへの **remoteInstall** フォルダーからの相対パスを指定します。 |
| [/BootImagepath: `<Relativepath>` ] | RemoteInstall フォルダからこのコンピュータが受信するブートイメージへの相対パスを指定します。 |

## <a name="examples"></a>例

12 の要求 Id を使用してコンピューターを承認するには、次のように入力します。

```
wdsutil /Approve-AutoaddDevices /RequestId:12
```

RequestID が20のコンピューターを承認し、指定した設定でイメージを展開するには、次のように入力します。

```
wdsutil /Approve-AutoaddDevices /RequestId:20 /MachineName:computer1 /OU:OU=Test,CN=company,DC=Domain,DC=Com /User:Domain\User1
/JoinRights:Full /ReferralServer:MyWDSServer /BootProgram:boot\x86\pxeboot.n12 /WdsClientUnattend:WDSClientUnattend\Unattend.xml /BootImagepath:boot\x86\images\boot.wim
```

承認保留中のすべてのコンピューターに、次のように入力します。

```
wdsutil /verbose /Approve-AutoaddDevices /RequestId:ALL
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wdsutil delete-autoadddevices コマンド](wdsutil-delete-autoadddevices.md)

- [wdsutil get-autoadddevices コマンド](wdsutil-get-autoadddevices.md)

- [wdsutil 拒否-autoadddevices コマンド](wdsutil-reject-autoadddevices.md)

- [Windows 展開サービスコマンドレット](/powershell/module/wds)
