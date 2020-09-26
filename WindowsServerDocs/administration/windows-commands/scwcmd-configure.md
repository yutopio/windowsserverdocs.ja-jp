---
title: scwcmd configure
description: セキュリティ構成ウィザード (SCW) で生成されたセキュリティポリシーをコンピューターに適用する scwcmd configure コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 6528b9dc-3d82-4228-b734-ed717458d74c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a57d2142f8fc7fd788a5669c5318ff6444c34734
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91388589"
---
# <a name="scwcmd-configure"></a>scwcmd configure

> 適用対象: Windows Server 2012 R2 および Windows Server 2012

コンピューターには、セキュリティ構成ウィザード SCW によって生成されたセキュリティ ポリシーを適用します。 このコマンド ライン ツールでは、入力としてコンピューター名の一覧も受け取ります。

## <a name="syntax"></a>構文

```
scwcmd configure [[[/m:<computername> | /ou:<OuName>] /p:<policy>] | /i:<computerlist>] [/u:<username>] [/pw:<password>] [/t:<threads>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| /m`<computername>` | NetBIOS 名、DNS 名、または構成するコンピューターの IP アドレスを指定します。 場合、 **/m** パラメーターが指定されている、 **/p** パラメーターも指定する必要があります。 |
| /ou`<OuName>` | Active Directory ドメイン サービスでは、組織単位 (OU) の完全修飾ドメイン名 (FQDN) を指定します。 場合、 **/ou** パラメーターが指定されている、 **/p** パラメーターも指定する必要があります。 OU 内のすべてのコンピューターは、指定されたポリシーに対して構成されます。 |
| /p`<policy>` | 構成の実行に使用する .xml ポリシー ファイルのパスとファイル名を指定します。 |
| /i`<computerlist>` | 予想されるポリシー ファイルと共にコンピューターの一覧を含む .xml ファイルのパスとファイル名を指定します。 .Xml ファイル内のすべてのコンピューターは、対応するポリシー ファイルに対して分析されます。 サンプル .xml ファイルはです `%windir%\security\SampleMachineList.xml` 。 |
| /u`<username>` | リモートコンピューターで構成を実行するときに使用する代替ユーザー資格情報を指定します。 既定値は、ユーザーには、ログオンしています。 |
| pw`<password>` | リモートコンピューターで構成を実行するときに使用する代替ユーザー資格情報を指定します。 既定値は、ログオン ユーザーのパスワードです。 |
| /t: `<threads>` | 分析中に保持する必要がある未処理の構成操作の同時実行数を指定します。 値の範囲は1-1000 で、既定値は40です。 |
| /l | ログに記録する分析処理を行われます。 1 つのログ ファイルが、分析するコンピューターごとに生成されます。 ログ ファイルは、結果のファイルと同じディレクトリに保存されます。 使用して、 **/o** 結果ファイルのディレクトリを指定するにはオプションです。 |
| /e | 不一致が検出された場合は、アプリケーション イベント ログにイベントを記録します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

## <a name="examples"></a>例

ファイル *webpolicy.xml*に対してセキュリティポリシーを構成するには、次のように入力します。

```
scwcmd configure /p:webpolicy.xml
```

*Webadmin*アカウントの資格情報を使用して、ファイル*webpolicy.xml*に対して*172.16.0.0*でコンピューターのセキュリティポリシーを構成するには、次のように入力します。

```
scwcmd configure /m:172.16.0.0 /p:webpolicy.xml /u:webadmin
```

*最大100のスレッド*で*campusmachines.xml*一覧のすべてのコンピューターでセキュリティポリシーを構成するには、次のように入力します。

```
scwcmd configure /i:campusmachines.xml /t:100
```

*Domainadmin*資格情報を使用して、ファイル*webpolicy.xml*に対して*WebServers OU*のセキュリティポリシーを構成するには、次のように入力します。

```
scwcmd configure /ou:OU=WebServers,DC=Marketing,DC=ABCCompany,DC=com /p:webpolicy.xml /u:DomainAdmin
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [scwcmd analyze コマンド](scwcmd-analyze.md)

- [scwcmd register コマンド](scwcmd-register.md)

- [scwcmd rollback コマンド](scwcmd-rollback.md)

- [scwcmd transform コマンド](scwcmd-transform.md)

- [scwcmd view コマンド](scwcmd-view.md)