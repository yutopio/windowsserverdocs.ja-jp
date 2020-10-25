---
title: wbadmin start sysrecovery
description: 指定されたパラメーターを使用してシステム回復 (ベアメタル回復) を実行する wbadmin start sysrecovery コマンドの参照記事です。
ms.topic: reference
ms.assetid: 95b8232f-7c42-452b-838e-15b0cf6faebe
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 292c0d6fc42f4fe58dda6a6fbbb6a693b70a8756
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524747"
---
# <a name="wbadmin-start-sysrecovery"></a>wbadmin start sysrecovery

指定されたパラメーターを使用して、システム回復 (ベアメタル回復) を実行します。

このコマンドを使用してシステムの回復を実行するには、 **Backup Operators** グループまたは **Administrators** グループのメンバーであるか、適切なアクセス許可が委任されている必要があります。

> [!IMPORTANT]
> **Wbadmin start sysrecovery**コマンドは、Windows 回復コンソールから実行する必要があります。 **wbadmin**ツールの既定の使用法のテキストには記載されていません。 詳細については、「 [Windows 回復環境 (WinRE)](/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)」を参照してください。

## <a name="syntax"></a>構文

```
wbadmin start sysrecovery -version:<VersionIdentifier> -backupTarget:{<BackupDestinationVolume> | <NetworkShareHostingBackup>}  [-machine:<BackupMachineName>] [-restoreAllVolumes] [-recreateDisks] [-excludeDisks] [-skipBadClusterCheck] [-quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -version | 復元するバックアップのバージョン識別子を MM/DD/YYYY-HH: MM 形式で指定します。 バージョン識別子がわからない場合は、 [wbadmin get versions コマンド](wbadmin-get-versions.md)を実行します。 |
| -backuptarget | 回復するバックアップが格納されている記憶域の場所を指定します。 このパラメーターは、このコンピューターのバックアップが通常格納されている場所とは異なる場所に保存されている場合に便利です。 |
| -コンピューター | バックアップの回復先となるコンピューターの名前を指定します。 **-BackupTarget**パラメーターが指定されている場合は、このパラメーターを使用する必要があります。 **-Machine**パラメーターは、複数のコンピューターが同じ場所にバックアップされている場合に便利です。 |
| -restoreAllVolumes | 選択したバックアップからすべてのボリュームを回復します。 このパラメーターが指定されていない場合、重要なボリューム (システム状態およびオペレーティングシステムコンポーネントを含むボリューム) のみが回復されます。 このパラメーターは、システムの回復中に重要ではないボリュームを回復する必要がある場合に便利です。 |
| -recreateDisks | バックアップの作成時に存在していた状態にディスク構成を回復します。<p>**警告:** このパラメーターは、オペレーティングシステムコンポーネントをホストするボリューム上のすべてのデータを削除します。 データボリュームからデータを削除することもできます。 |
| -excludeDisks | **-Recreatedisks**パラメーターと共に指定した場合にのみ有効です。これは、 [wbadmin get disks コマンド](wbadmin-get-disks.md)の出力に示されているように、ディスク識別子のコンマ区切りリストとして入力する必要があります。 除外されたディスクはパーティション分割またはフォーマットされません。 このパラメーターは、復旧操作中に変更したくないディスク上のデータを保持するのに役立ちます。 |
| -skipBadClusterCheck | ボリュームを回復する場合にのみ有効です。 無効なクラスター情報について、回復先のディスクのチェックをスキップします。 別のサーバーまたはハードウェアに回復する場合は、このパラメーターを使用しないことをお勧めします。 これらのディスクに対して **chkdsk/b** コマンドをいつでも手動で実行して、不良クラスターがないかどうかを確認し、それに応じてファイルシステム情報を更新することができます。<p>**重要:****Chkdsk/b**を実行するまでは、回復したシステムで報告された不良クラスターが正確でない可能性があります。 |
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

## <a name="examples"></a>例

2020年3月31日に9:00 午前5時に実行されたバックアップからの情報の回復を開始するには、次のように入力します。

```
wbadmin start sysrecovery -version:03/31/2020-09:00 -backupTarget:d:
```

2020年4月30日に実行されたバックアップからの情報の回復を開始するには、server01 の共有フォルダーにある9:00 午前5時に、 `\\servername\share` 次のように入力します。

```
wbadmin start sysrecovery -version:04/30/2020-09:00 -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [WBBareMetalRecovery](/powershell/module/windowserverbackup/Get-WBBareMetalRecovery)
