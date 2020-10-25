---
title: wbadmin start recovery
description: 指定したパラメーターに基づいて回復操作を実行する wbadmin start recovery コマンドの参照記事です。
ms.topic: reference
ms.assetid: 52381316-a0fa-459f-b6a6-01e31fb21612
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 408ccadd830e50e9b51447cc19f7243d349cb3ef
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524757"
---
# <a name="wbadmin-start-recovery"></a>wbadmin start recovery

指定したパラメーターに基づいて回復操作を実行します。

このコマンドを使用して回復を実行するには、 **Backup Operators** グループまたは **Administrators** グループのメンバーであるか、適切なアクセス許可が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

## <a name="syntax"></a>構文

```
wbadmin start recovery -version:<VersionIdentifier> -items:{<VolumesToRecover> | <AppsToRecover> | <FilesOrFoldersToRecover>} -itemtype:{Volume | App | File} [-backupTarget:{<VolumeHostingBackup> | <NetworkShareHostingBackup>}] [-machine:<BackupMachineName>] [-recoveryTarget:{<TargetVolumeForRecovery> | <TargetPathForRecovery>}] [-recursive] [-overwrite:{Overwrite | CreateCopy | Skip}] [-notRestoreAcl] [-skipBadClusterCheck] [-noRollForward] [-quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -version | 復元するバックアップのバージョン識別子を MM/DD/YYYY-HH: MM 形式で指定します。 バージョン識別子がわからない場合は、 [wbadmin get versions コマンド](wbadmin-get-versions.md)を実行します。 |
| -項目 | 回復するボリューム、アプリ、ファイル、またはフォルダーのコンマ区切りの一覧を指定します。 このパラメーターは、 **-itemtype** パラメーターと共に使用する必要があります。 |
| -itemtype | 回復する項目の種類を指定します。 **ボリューム**、**アプリ**、または**ファイル**である必要があります。 **-Itemtype**が*volume*の場合、ボリュームドライブ文字、ボリュームマウントポイント、または GUID ベースのボリューム名を指定することによって、ボリュームを1つだけ指定できます。 **-Itemtype**が*App*の場合は、1つのアプリケーションのみを指定することも、値の設定を使用して Active Directory の**インストールを回復**することもできます。 回復するには、アプリが Windows Server バックアップに登録されている必要があります。 **-Itemtype**が*ファイル*の場合は、ファイルまたはフォルダーを指定できますが、同じボリュームの一部である必要があり、同じ親フォルダーの下にある必要があります。 |
| -backuptarget | 回復するバックアップが格納されている記憶域の場所を指定します。 このパラメーターは、このコンピューターのバックアップが通常格納されている場所とは異なる場所にある場合に便利です。 |
| -コンピューター | バックアップの回復先となるコンピューターの名前を指定します。 **-BackupTarget**パラメーターが指定されている場合は、このパラメーターを使用する必要があります。 **-Machine**パラメーターは、複数のコンピューターが同じ場所にバックアップされている場合に便利です。 |
| -recoveryTarget | 復元先の場所を指定します。 このパラメーターは、この場所が以前にバックアップされた場所と異なる場合に便利です。 また、ボリューム、ファイル、またはアプリの復元に使用することもできます。 ボリュームを復元する場合は、代替ボリュームのボリュームドライブ文字を指定できます。 ファイルまたはアプリを復元する場合は、別の回復場所を指定できます。 |
| -recursive | ファイルを回復する場合にのみ有効です。 フォルダー内のファイルと、指定したフォルダーの下位にあるすべてのファイルを回復します。 既定では、指定されたフォルダーに直接存在するファイルのみが回復されます。 |
|-上書き | ファイルを回復する場合にのみ有効です。 回復中のファイルが同じ場所に既に存在する場合に実行する操作を指定します。 有効なオプションは次のとおりです。<ul><li>**Skip** -Windows Server バックアップによって既存のファイルがスキップされ、次のファイルの回復が続行されます。</li><li>**"Createcopy"** -既存のファイルが変更されないように、既存のファイルのコピーを作成 Windows Server バックアップします。</li><li>**Overwrite** -Windows Server バックアップによって、バックアップからのファイルで既存のファイルが上書きされます。 |
| -notRestoreAcl | ファイルを回復する場合にのみ有効です。 バックアップから回復するファイルのセキュリティアクセス制御リスト (Acl) を復元しないように指定します。 既定では、セキュリティ Acl が復元されます (既定値は **true**です)。 このパラメーターを使用すると、復元されたファイルの Acl は、ファイルの復元先の場所から継承されます。 |
| -skipBadClusterCheck | ボリュームを回復する場合にのみ有効です。 無効なクラスター情報について、回復先のディスクのチェックをスキップします。 別のサーバーまたはハードウェアに回復する場合は、このパラメーターを使用しないことをお勧めします。 これらのディスクに対して **chkdsk/b** コマンドをいつでも手動で実行して、不良クラスターがないかどうかを確認し、それに応じてファイルシステム情報を更新することができます。<p>**重要:****Chkdsk/b**を実行するまでは、回復したシステムで報告された不良クラスターが正確でない可能性があります。 |
| -noRollForward | アプリを回復する場合にのみ有効です。 バックアップから最新バージョンを選択した場合に、以前のアプリの特定の時点への回復を許可します。 以前の特定の時点への復旧は、アプリの他のすべての非最新バージョンの既定値として実行されます。 |
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

#### <a name="remarks"></a>解説

- 特定のバックアップバージョンから回復可能な項目の一覧を表示するには、 [wbadmin get items コマンド](wbadmin-get-items.md)を実行します。 バックアップ時にボリュームにマウントポイントまたはドライブ文字がない場合、このコマンドは、ボリュームの回復に使用する GUID ベースのボリューム名を返します。

- [メディア **からのインストール** ] 操作を実行して、Active Directory Domain Services に必要な関連データを回復するには、次のような値を使用して、Active Directory データベース、レジストリ、および SYSVOL の状態のコピー **を作成し** 、この情報を **-recoverytarget**で指定された場所に保存します。 このパラメーターは **、-recoverytarget** が指定されている場合にのみ使用してください。

## <a name="examples"></a>例

2020年3月31日の午前9:00 に撮影されたバックアップの回復を実行するには、次のように入力します。

```
wbadmin start recovery -version:03/31/2020-09:00 -itemType:Volume -items:d:
```

2020年3月31日のバックアップを実行するには、レジストリの午前9:00 に、次のように入力します。

```
wbadmin start recovery -version:03/31/2020-09:00 -itemType:App -items:Registry -recoverytarget:d:\
```

9:00 2020 年3月31日から、d:\folder の下位にある d:\folder とフォルダーのバックアップの回復を実行するには、次のように入力します。

```
wbadmin start recovery -version:03/31/2020-09:00 -itemType:File -items:d:\folder -recursive
```

2020年3月31日の午前9:00 に撮影したバックアップの回復を実行するには、次のように `\\?\Volume{cc566d14-44a0-11d9-9d93-806e6f6e6963}\` 入力します。

```
wbadmin start recovery -version:03/31/2020-09:00 -itemType:Volume -items:\\?\Volume{cc566d14-44a0-11d9-9d93-806e6f6e6963}\
```

9:00 2020 年4月30日から、server01 からの共有フォルダーのバックアップの回復を実行するには `\\servername\share` 、次のように入力します。

```
wbadmin start recovery -version:04/30/2020-09:00 -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [WBFileRecovery](/powershell/module/windowserverbackup/Start-WBFileRecovery)

- [WBHyperVRecovery](/powershell/module/windowserverbackup/Start-WBHyperVRecovery)

- [WBSystemStateRecovery](/powershell/module/windowserverbackup/Start-WBSystemStateRecovery)

- [WBVolumeRecovery](/powershell/module/windowserverbackup/Start-WBVolumeRecovery)
