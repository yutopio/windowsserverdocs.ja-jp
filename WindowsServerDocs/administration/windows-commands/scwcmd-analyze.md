---
title: scwcmd analyze
description: Scwcmd analyze コマンドの参照記事。コンピューターがポリシーに準拠しているかどうかを判断します。
ms.topic: reference
ms.assetid: 0259271b-be5b-48d7-a51d-8b9b6786efb4
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0d891262ebf04b1b8e604bc4756a3ca05888f8fa
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388608"
---
# <a name="scwcmd-analyze"></a>scwcmd analyze

> 適用対象: Windows Server 2012 R2 および Windows Server 2012

コンピューターが、ポリシーに準拠しているかどうかを判断します。 .Xml ファイルには、結果が返されます。

このコマンドでは、入力としてコンピューター名の一覧を受け取ることもできます。 ブラウザーで結果を表示するには、 **scwcmd view** を使用し、 `%windir%\security\msscw\TransformFiles\scwanalysis.xsl` .xsl 変換としてを指定します。

## <a name="syntax"></a>構文

```
scwcmd analyze [[[/m:<computername> | /ou:<OuName>] /p:<policy>] | /i:<computerlist>] [/o:<resultdir>] [/u:<username>] [/pw:<password>] [/t:<threads>] [/l] [/e]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /m`<computername>` | NetBIOS 名、DNS 名、または分析するコンピューターの IP アドレスを指定します。 場合、 **/m** パラメーターが指定されている、 **/p** パラメーターも指定する必要があります。 |
| /ou`<OuName>` | Active Directory ドメイン サービスでは、組織単位 (OU) の完全修飾ドメイン名 (FQDN) を指定します。 場合、 **/ou** パラメーターが指定されている、 **/p** パラメーターも指定する必要があります。 OU 内のすべてのコンピューターが特定のポリシーに対して分析されます。 |
| /p`<policy>` | 分析の実行に使用する .xml ポリシー ファイルのパスとファイル名を指定します。 |
| /i`<computerlist>` | 予想されるポリシー ファイルと共にコンピューターの一覧を含む .xml ファイルのパスとファイル名を指定します。 .Xml ファイル内のすべてのコンピューターは、対応するポリシー ファイルに対して分析されます。 サンプル .xml ファイルはです `%windir%\security\SampleMachineList.xml` 。 |
| /o`<resultdir>` | 分析結果ファイルの保存先ディレクトリとパスを指定します。 既定値は、現在のディレクトリです。 |
| /u`<username>` | リモート コンピューターで、分析を実行するときに使用する、代替のユーザー資格情報を指定します。 既定値は、ユーザーには、ログオンしています。 |
| pw`<password>` | リモート コンピューターで、分析を実行するときに使用する、代替のユーザー資格情報を指定します。 既定値は、ログオン ユーザーのパスワードです。 |
| /t: `<threads>` | 分析中に保持する必要のある未処理の分析操作の数を指定します。 値の範囲は1-1000 で、既定値は40です。 |
| /l | ログに記録する分析処理を行われます。 1 つのログ ファイルが、分析するコンピューターごとに生成されます。 ログ ファイルは、結果のファイルと同じディレクトリに保存されます。 使用して、 **/o** 結果ファイルのディレクトリを指定するにはオプションです。 |
| /e | 不一致が検出された場合は、アプリケーション イベント ログにイベントを記録します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

ファイル *webpolicy.xml*に対してセキュリティポリシーを分析するには、次のように入力します。

```
scwcmd analyze /p:webpolicy.xml
```

*Webadmin*アカウントの資格情報を使用して、ファイル*webpolicy.xml*に対して*webserver*という名前のコンピューター上のセキュリティポリシーを分析するには、次のように入力します。

```
scwcmd analyze /m:webserver /p:webpolicy.xml /u:webadmin
```

ファイル *webpolicy.xml*に対して、 *最大100のスレッド*でセキュリティポリシーを分析し、結果をという名前のファイルに出力するに *は、* 次のように入力します。

```
scwcmd analyze /i:webpolicy.xml /t:100 /o:\\resultserver\results
```

*Domainadmin*資格情報を使用して、ファイル*webpolicy.xml*に対して*WebServers OU*のセキュリティポリシーを分析するには、次のように入力します。

```
scwcmd analyze /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [scwcmd configure コマンド](scwcmd-configure.md)

- [scwcmd register コマンド](scwcmd-register.md)

- [scwcmd rollback コマンド](scwcmd-rollback.md)

- [scwcmd transform コマンド](scwcmd-transform.md)

- [scwcmd view コマンド](scwcmd-view.md)