---
title: wbadmin start systemstaterecovery
description: Wbadmin start systemstaterecovery コマンドの参照記事。ここでは、指定した場所へのシステム状態の回復を実行します。
ms.topic: reference
ms.assetid: 208b1be9-3452-4aba-bb49-46bc587fca96
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: b52b4fedf14eb2d4caab4e9d521767ff9e89365a
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524717"
---
# <a name="wbadmin-start-systemstaterecovery"></a>wbadmin start systemstaterecovery

指定したバックアップから、場所とシステム状態の回復を実行します。

このコマンドを使用してシステム状態の回復を実行するには、 **Backup Operators** グループまたは **Administrators** グループのメンバーであるか、適切なアクセス許可が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

> [!NOTE]
> Windows Server バックアップは、システム状態のバックアップまたはシステム状態の回復の一部として、レジストリユーザーハイブ (HKEY_CURRENT_USER) をバックアップまたは回復しません。

## <a name="syntax"></a>構文

```
wbadmin start systemstaterecovery -version:<VersionIdentifier> -showsummary [-backupTarget:{<BackupDestinationVolume> | <NetworkSharePath>}]
[-machine:<BackupMachineName>] [-recoveryTarget:<TargetPathForRecovery>] [-authsysvol] [-autoReboot] [-quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -version | 復元するバックアップのバージョン識別子を MM/DD/YYYY-HH: MM 形式で指定します。 バージョン識別子がわからない場合は、 [wbadmin get versions コマンド](wbadmin-get-versions.md)を実行します。 |
| -showsummary | 最後のシステム状態の回復の概要を報告します (操作を完了するために再起動が必要になった後)。 このパラメーターを他のパラメーターと共に指定することはできません。 |
| -backuptarget | 回復するバックアップが格納されている記憶域の場所を指定します。 このパラメーターは、バックアップが通常格納される場所とストレージの場所が異なる場合に便利です。 |
| -コンピューター | バックアップを回復するコンピューターの名前を指定します。 **-BackupTarget**パラメーターが指定されている場合は、このパラメーターを使用する必要があります。 **-Machine**パラメーターは、複数のコンピューターが同じ場所にバックアップされている場合に便利です。 |
| -recoveryTarget | 復元先のディレクトリを指定します。 このパラメーターは、バックアップを別の場所に復元する場合に便利です。 |
| -authsysvol | システムボリューム (sysvol) の共有ディレクトリの authoritative restore を実行します。 |
| -autoReboot | システム状態の回復操作の最後にシステムを再起動することを指定します。 このパラメーターは、元の場所への回復に対してのみ有効です。 回復操作の後で手順を実行する必要がある場合は、このパラメーターを使用しないことをお勧めします。 |
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

## <a name="examples"></a>例

03/31/2020 の午前9:00 にバックアップのシステム状態の回復を開始するには、次のように入力します。

```
wbadmin start systemstaterecovery -version:03/31/2020-09:00
```

04/30/2020 の午前9:00 にバックアップのシステム状態の回復を開始するには server01 の共有リソースに格納されている `\\servername\share` 、次のように入力します。

```
wbadmin start systemstaterecovery -version:04/30/2013-09:00 -backupTarget:\\servername\share -machine:server01
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [WBSystemStateRecovery](/powershell/module/windowserverbackup/Start-WBSystemStateRecovery)
