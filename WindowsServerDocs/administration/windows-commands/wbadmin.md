---
title: wbadmin
description: コマンドプロンプトからオペレーティングシステム、ボリューム、ファイル、フォルダー、およびアプリケーションをバックアップして復元できるようにする wbadmin コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 4b0b3f32-d21f-4861-84bb-b2eadbf1e7b8
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: df96e85d7cb4999088efe9bd6ede70087cd24cb7
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524667"
---
# <a name="wbadmin"></a>wbadmin

では、コマンドプロンプトからオペレーティングシステム、ボリューム、ファイル、フォルダー、およびアプリケーションをバックアップおよび復元できます。

このコマンドを使用して定期的にスケジュールされたバックアップを構成するには、 **Administrators** グループのメンバーである必要があります。 このコマンドを使用して他のすべてのタスクを実行するには、 **Backup Operators** グループまたは **Administrators** グループのメンバであるか、適切な権限が委任されている必要があります。

**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

## <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| [wbadmin delete catalog](wbadmin-delete-catalog.md) | ローカル コンピューター上のバックアップ カタログを削除します。 このコマンドは、このコンピューターでバックアップ カタログが壊れているか、カタログの復元に使用できる別の場所に格納されているバックアップがない場合はのみに使用します。 |
| [wbadmin delete systemstatebackup](wbadmin-delete-systemstatebackup.md) | 1つまたは複数のシステム状態のバックアップを削除します。 |
| [wbadmin disable backup](wbadmin-disable-backup.md) | 毎日のバックアップを無効にします。 |
| [wbadmin enable backup](wbadmin-enable-backup.md) | 定期的にスケジュールされたバックアップを構成して有効にします。 |
| [wbadmin get disks](wbadmin-get-disks.md) | 現在オンラインになっているディスクを一覧表示します。 |
| [wbadmin get items](wbadmin-get-items.md) | バックアップに含まれる項目を一覧表示します。 |
| [wbadmin get status](wbadmin-get-status.md) | 現在実行中のバックアップまたは回復操作の状態が表示されます。 |
| [wbadmin get versions](wbadmin-get-versions.md) | ローカルコンピューターから回復可能なバックアップの詳細を一覧表示するか、別の場所が指定されている場合は、別のコンピューターから復元します。 |
| [wbadmin restore catalog](wbadmin-restore-catalog.md) | ローカルコンピューター上のバックアップカタログが破損している場合に、指定した記憶域の場所からバックアップカタログを回復します。 |
| [wbadmin start backup](wbadmin-start-backup.md) | 1回限りのバックアップを実行します。 パラメーターを使用しない場合は、毎日のバックアップスケジュールの設定が使用されます。 |
| [wbadmin start recovery](wbadmin-start-recovery.md) | 指定されたボリューム、アプリケーション、ファイル、またはフォルダーの回復を実行します。 |
| [wbadmin start sysrecovery](wbadmin-start-sysrecovery.md) | (少なくともすべてのボリュームをオペレーティング システムの状態を含む) 完全なシステムの回復を実行します。 このコマンドは、Windows 回復環境を使用している場合にのみ使用できます。 |
| [wbadmin start systemstatebackup](wbadmin-start-systemstatebackup.md) | システム状態のバックアップを実行します。 |
| [wbadmin start systemstaterecovery](wbadmin-start-systemstaterecovery.md) | システム状態の回復を実行します。 |
| [wbadmin stop job](wbadmin-stop-job.md) | 現在実行中のバックアップまたは回復操作を停止します。 |

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [Windows PowerShell の Windows Server バックアップコマンドレット](/powershell/module/windowsserverbackup)

- [Windows 回復環境 (WinRE)](/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
