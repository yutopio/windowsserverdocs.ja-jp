---
title: wbadmin get items
description: 特定のバックアップに含まれる項目を一覧表示する wbadmin get items コマンドの参照記事です。
ms.topic: reference
ms.assetid: 27d08ce3-6e06-4260-b264-fc1bde132d09
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 5eda5977c0c7606f0e1031894360a06205044656
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92155876"
---
# <a name="wbadmin-get-items"></a>wbadmin get items

特定のバックアップに含まれるアイテムを一覧表示します。

このコマンドを使用して特定のバックアップに含まれる項目を一覧表示するには、 **Backup Operators** グループまたは **Administrators** グループのメンバーであるか、適切なアクセス許可が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

## <a name="syntax"></a>構文

```
wbadmin get items -version:<VersionIdentifier> [-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}] [-machine:<BackupMachineName>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -version | バックアップのバージョンを MM/DD/YYYY-HH: MM 形式で指定します。 バージョン情報がわからない場合は、 [wbadmin get versions](wbadmin-get-versions.md) コマンドを実行します。 |
| -backuptarget | 詳細を表示するバックアップが格納されている場所を指定します。 対象の場所に格納されているバックアップを一覧表示するには、を使用します。 バックアップターゲットの場所には、ローカルに接続されたディスクドライブまたはリモート共有フォルダーを指定できます。 バックアップが作成されたのと同じコンピューターでこのコマンドを実行する場合、このパラメーターは必要ありません。 ただし、別のコンピューターから作成されたバックアップに関する情報を取得するには、このパラメーターが必要です。 |
| -コンピューター | バックアップの詳細を表示するコンピューターの名前を指定します。 複数のコンピューターが同じ場所にバックアップされている場合に利用できます。 **-BackupTarget**が指定されている場合は、を使用する必要があります。 |

## <a name="examples"></a>使用例

2013年3月31日の午前9:00 に実行されたバックアップの項目を一覧表示するには、次のように入力します。

```
wbadmin get items -version:03/31/2013-09:00
```

2013年4月30日に実行された server01 のバックアップからの項目を一覧表示するには、午前9:00 に をに格納し `\\<servername>\<share>` 、次のように入力します。

```
wbadmin get items -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [wbadmin get バージョンコマンド](wbadmin-get-versions.md)

- [WBBackupSet](/powershell/module/windowserverbackup/Get-WBBackupSet)
