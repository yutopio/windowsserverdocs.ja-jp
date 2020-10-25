---
title: wbadmin start systemstatebackup
description: Wbadmin start systemstatebackup コマンドの参照記事。このコマンドは、ローカルコンピューターのシステム状態のバックアップを作成し、指定された場所に保存します。
ms.topic: reference
ms.assetid: 998366c1-0a64-45e6-9ed3-4c3f5b8406f0
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: afdfb3f4a52ae0f5897517f8d59069bea820bc4a
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524727"
---
# <a name="wbadmin-start-systemstatebackup"></a>wbadmin start systemstatebackup

ローカルコンピューターのシステム状態のバックアップを作成し、指定した場所に保存します。

このコマンドを使用してシステム状態のバックアップを実行するには、 **Backup Operators** グループまたは **Administrators** グループのメンバであるか、適切な権限が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

> [!NOTE]
> Windows Server バックアップは、システム状態のバックアップまたはシステム状態の回復の一部として、レジストリユーザーハイブ (HKEY_CURRENT_USER) をバックアップまたは回復しません。

## <a name="syntax"></a>構文

```
wbadmin start systemstatebackup -backupTarget:<VolumeName> [-quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -backuptarget | バックアップを保存する場所を指定します。 記憶域の場所には、ドライブ文字またはという形式の GUID ベースのボリュームが必要です `\\?\Volume{*GUID*}` 。 `-backuptarget:\\servername\sharedfolder\`システム状態のバックアップを格納するには、コマンドを使用します。 |
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

## <a name="examples"></a>例

システム状態のバックアップを作成し、ボリューム f に保存するには、次のように入力します。

```
wbadmin start systemstatebackup -backupTarget:f:
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [WBBackup](/powershell/module/windowserverbackup/Start-WBBackup)
