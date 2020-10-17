---
title: wbadmin get versions
description: ローカルコンピューターまたは別のコンピューターに格納されている利用可能なバックアップの詳細を一覧表示する wbadmin get versions コマンドの参照記事です。
ms.topic: reference
ms.assetid: b986acc4-d083-4d32-9434-862314ed5e97
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 6825b515f028046702283a2374de26100fd3015f
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92155924"
---
# <a name="wbadmin-get-versions"></a>wbadmin get versions

ローカルコンピューターまたは別のコンピューターに格納されている利用可能なバックアップの詳細を一覧表示します。 バックアップの詳細には、バックアップ時刻、バックアップの保存場所、バージョン識別子、および実行できる回復の種類が含まれます。

このコマンドを使用して使用可能なバックアップの詳細を取得するには、 **Backup Operators** グループまたは **Administrators** グループのメンバであるか、適切な権限が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

パラメーターを指定せずにこのコマンドを使用すると、バックアップが使用できない場合でも、ローカルコンピューターのすべてのバックアップが一覧表示されます。

## <a name="syntax"></a>構文

```
wbadmin get versions [-backupTarget:{<BackupTargetLocation> | <NetworkSharePath>}] [-machine:BackupMachineName]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -backuptarget | 詳細を表示するバックアップが格納されている場所を指定します。 対象の場所に格納されているバックアップを一覧表示するには、を使用します。 バックアップターゲットの場所は、ローカルに接続されたディスクドライブ、ボリューム、リモート共有フォルダー、リムーバブルメディア (DVD ドライブなど)、またはその他の光学メディアにすることができます。 バックアップが作成されたのと同じコンピューターでこのコマンドを実行する場合、このパラメーターは必要ありません。 ただし、別のコンピューターから作成されたバックアップに関する情報を取得するには、このパラメーターが必要です。 |
| -コンピューター | バックアップの詳細を表示するコンピューターを指定します。 複数のコンピューターのバックアップが同じ場所に格納されている場合に使用します。 **-BackupTarget**が指定されている場合は、を使用する必要があります。 |

## <a name="examples"></a>使用例

ボリューム H: に格納されている利用可能なバックアップの一覧を表示するには、次のように入力します。

```
wbadmin get versions -backupTarget:H:
```

コンピューター server01 のリモート共有フォルダーに格納されている利用可能なバックアップの一覧を表示するには `\\<servername>\<share>` 、次のように入力します。

```
wbadmin get versions -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [wbadmin get items コマンド](wbadmin-get-items.md)

- [WBBackupTarget](/powershell/module/windowserverbackup/Get-WBBackupTarget)
