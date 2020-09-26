---
title: servermanagercmd
description: Servermanagercmd.exe コマンドの参照記事。役割、役割サービス、および機能をインストールして削除します。
ms.topic: reference
ms.assetid: 507c4b87-8e13-4872-8b34-0c7508eecbc1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 07/11/2018
ms.openlocfilehash: 4a00294b70728a41cc68ae15d35a8c19fd768cf7
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389160"
---
# <a name="servermanagercmd"></a>servermanagercmd

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

インストールし、役割、役割サービス、および機能を削除します。 すべての役割、役割サービス、および使用可能な機能の一覧が表示され、このコンピューターにインストールされているかを示します。

> [!IMPORTANT]
> このコマンド servermanagercmd.exe は非推奨とされており、Windows の将来のリリースでサポートされるとは限りません。 代わりに、サーバーマネージャーに使用できる Windows PowerShell コマンドレットを使用することをお勧めします。 詳しくは、「[役割、役割サービス、または機能のインストールまたはアンインストール](/administration/server-manager/install-or-uninstall-roles-role-services-or-features)」をご覧ください。

## <a name="syntax"></a>構文

```
servermanagercmd -query [[[<drive>:]<path>]<query.xml>] [-logpath [[<drive>:]<path>]<log.txt>]
servermanagercmd -inputpath  [[[<drive>:]<path>]<answer.xml>] [-resultpath <result.xml> [-restart] | -whatif] [-logpath [[<drive>:]<path>]<log.txt>]
servermanagercmd -install <id> [-allSubFeatures] [-resultpath [[<drive>:]<path>]<result.xml> [-restart] | -whatif] [-logpath [[<Drive>:]<path>]<log.txt>]
servermanagercmd -remove <id> [-resultpath <result.xml> [-restart] | -whatif] [-logpath  [[<drive>:]<path>]<log.txt>]
servermanagercmd [-help | -?]
servermanagercmd -version
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| -クエリ `[[[<drive>:]<path>]<query.xml>]` | サーバー上のすべての役割、役割サービス、およびインストールされ、インストール可能な機能の一覧を表示します。 このパラメーターの短い形式を使用することもできます。 **-q**します。 クエリ結果を XML ファイルに保存する場合は、置換する XML ファイルを指定し `<query.xml>` ます。 |
| -inputpath  `[[[<drive>:]<path>]<answer.xml>]` | によって表される XML 応答ファイルで指定された役割、役割サービス、および機能をインストールまたは削除し `<answer.xml>` ます。 このパラメーターの短い形式を使用することもできます。 **-p します。** |
| -インストール `<id>` | によって指定された役割、役割サービス、または機能をインストール `<id>` します。 識別子が区別されます。 複数の役割、役割サービス、および機能は、スペースで区切る必要があります。 次の省略可能なパラメーターは、 **-install** パラメーターと共に使用されます。<ul><li>**-設定** `<SettingName>=<SettingValue>` -インストールに必要な設定を指定します。</li><li>**-allsubfeatures** -下位のすべてのサービスと機能のインストールを、親の役割、役割サービス、または値に指定された機能と共に指定し `<id>` ます。<p>**注**<br>一部のロールコンテナーには、すべての役割サービスのインストールを許可するコマンドライン識別子がありません。 これは、サーバー マネージャーのコマンドの同じインスタンスでは、役割サービスをインストールできない場合に大文字と小文字です。 たとえば、active directory フェデレーションサービスとフェデレーションサービスプロキシの役割サービスのフェデレーションサービスの役割サービスは、同じサーバーマネージャーコマンドインスタンスを使用してインストールすることはできません。</li><li>**-resultpath** `<result.xml>` -インストールの結果をで表される XML ファイルに保存 `<result.xml>` します。 このパラメーターの短い形式を使用することもできます。 **-r**します。<p>**注**<br>**-Resultpath**パラメーターと **-whatif**パラメーターの両方を指定して servermanagercmd.exe を実行することはできません。</li><li>**-restart** -インストールが完了すると、コンピューターを自動的に再起動します (インストールされている役割または機能によって再起動が必要な場合)。</li><li>**-whatif** - **-install** パラメーターに指定されたすべての操作を表示します。 **-Whatif**パラメーターの短い形式 ( **-w**) を使用することもできます。 **-Resultpath**パラメーターと **-whatif**パラメーターの両方を指定して**servermanagercmd.exe**を実行することはできません。</li><li>**-logpath** `<[[<drive>:]<path>]<log.txt>>` -既定値以外のログファイルの名前と場所を指定し `%windir%\temp\servermanager.log` ます。</li></ul> |
| -削除 `<id>` | によって指定された役割、役割サービス、または機能を削除 `<id>` します。 識別子が区別されます。 複数の役割、役割サービス、および機能は、スペースで区切る必要があります。 次の省略可能なパラメーターは、 **-remove** パラメーターと共に使用されます。<ul><li>**-resultpath** `<[[<drive>:]<path>]result.xml>` -削除の結果をで表される XML ファイルに保存 `<result.xml>` します。 このパラメーターの短い形式を使用することもできます。 **-r**します。<p>**注**<br>**-Resultpath**と **-whatif**パラメーターの両方を指定して servermanagercmd.exe を実行することはできません。</li><li>**-restart** -削除が完了すると、コンピューターを自動的に再起動します (残りの役割または機能によって再起動が必要な場合)。</li><li>**-whatif** --remove パラメーターに指定されたすべての操作を表示します。 -Whatif パラメーターの短い形式 ( **-w**) を使用することもできます。 **-Resultpath**と **-whatif**パラメーターの両方を指定して servermanagercmd.exe を実行することはできません。</li><li>**-logpath** `<[[<Drive>:]<path>]<log.txt>>`-既定値以外のログファイルの名前と場所を指定し `%windir%\temp\servermanager.log` ます。</li></ul> |
| -version | サーバー マネージャーのバージョン番号を表示します。 短い形式を使用することもできます。 **-v**します。 |
| -help | コマンドプロンプトウィンドウにヘルプを表示します。 短い形式を使用することもできます。 **-?** します。 |

## <a name="examples"></a>例

使用可能なすべての役割、役割サービス、および機能と、コンピューターにインストールされている役割、役割サービス、および機能の一覧を表示するには、次のように入力します。

```
servermanagercmd -query
```

Web サーバー (IIS) の役割をインストールし、 *installResult.xml*で表される XML ファイルにインストール結果を保存するには、次のように入力します。

```
servermanagercmd -install Web-Server -resultpath installResult.xml
```

*install.xml*によって表される XML 応答ファイルで指定されている手順に基づいて、インストールまたは削除される役割、役割サービス、および機能に関する詳細情報を表示するには、次のように入力します。

```
servermanagercmd -inputpath install.xml -whatif
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [サーバーマネージャーの概要](/administration/server-manager/server-manager)
