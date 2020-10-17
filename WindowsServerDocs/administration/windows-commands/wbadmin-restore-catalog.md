---
title: wbadmin restore catalog
description: 指定したストレージの場所からローカルコンピューターのバックアップカタログを回復する、wbadmin restore catalog コマンドの参照記事です。
ms.topic: reference
ms.assetid: ce1e24a0-821d-4353-b09d-8f82c5c4ad56
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 046c4b4162c9512d5893c3c06e83e7260386c990
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92155863"
---
# <a name="wbadmin-restore-catalog"></a>wbadmin restore catalog

指定した記憶域の場所からローカルコンピューターのバックアップカタログを回復します。

このコマンドを使用して、特定のバックアップに含まれているバックアップカタログを回復するには、 **Backup Operators** グループまたは **Administrators** グループのメンバーであるか、適切なアクセス許可が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

> [!NOTE]
> バックアップを保存する場所 (ディスク、DVD、またはリモート共有フォルダー) が破損または失われ、バックアップカタログの復元に使用できない場合は、 [wbadmin delete catalog](wbadmin-delete-catalog.md) コマンドを実行して、破損したカタログを削除します。 この場合は、バックアップカタログを削除した後で、新しいバックアップを作成することをお勧めします。

## <a name="syntax"></a>構文

```
wbadmin restore catalog -backupTarget:{<BackupDestinationVolume> | <NetworkShareHostingBackup>} [-machine:<BackupMachineName>] [-quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -backuptarget | バックアップが作成された時点でのシステムのバックアップカタログの場所を指定します。 |
| -コンピューター | バックアップカタログを回復するコンピューターの名前を指定します。 複数のコンピューターのバックアップが同じ場所に格納されている場合は、を使用します。 **-BackupTarget**が指定されている場合は、を使用する必要があります。 |
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

## <a name="examples"></a>使用例

ディスク D: に格納されているバックアップからカタログを復元するには、次のように入力します。

```
wbadmin restore catalog -backupTarget:D
```

Server01 の共有フォルダーに格納されているバックアップからカタログを復元するには、次のように `\\<servername>\<share>` 入力します。

```
wbadmin restore catalog -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [wbadmin delete カタログコマンド](wbadmin-delete-catalog.md)

- [復元-WBCatalog](/powershell/module/windowserverbackup/Restore-WBCatalog)
