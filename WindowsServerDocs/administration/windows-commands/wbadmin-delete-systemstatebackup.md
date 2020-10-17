---
title: wbadmin delete systemstatebackup
description: 指定したシステム状態のバックアップを削除する wbadmin delete systemstatebackup コマンドの参照記事です。
ms.topic: reference
ms.assetid: 707d37cb-448d-4542-b6ac-1fc89e749788
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 05ce1e2deb8a2466df70b56a43c4532871d491b9
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156072"
---
# <a name="wbadmin-delete-systemstatebackup"></a>wbadmin delete systemstatebackup

指定したシステム状態のバックアップを削除します。 指定したボリュームがローカル サーバーのシステム状態バックアップ以外のバックアップを含んでいる場合、それらのバックアップは削除されません。

このコマンドを使用してシステム状態のバックアップを削除するには、 **Backup Operators** グループまたは **Administrators** グループのメンバであるか、適切な権限が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

> [!NOTE]
> Windows Server バックアップはバックアップまたはシステム状態のバックアップまたはシステム状態の回復の一部としてユーザーのレジストリ ハイブ (HKEY_CURRENT_USER) を回復します。

## <a name="syntax"></a>構文

```
wbadmin delete systemstatebackup {-keepVersions:<numberofcopies> | -version:<versionidentifier> | -deleteoldest} [-backupTarget:<volumename>] [-machine:<backupmachinename>] [-quiet]
```

> [!IMPORTANT]
> 次のパラメーターのいずれかを指定する必要があります: **-keepversions**、 **-version**、 **-deleteoldest**。

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -keepVersions | 最新のシステム状態バックアップを保持する数を指定します。 この値は、正の整数にする必要があります。 パラメーター値 **-keepversions: 0** を指定すると、すべてのシステム状態のバックアップが削除されます。 |
| -version | 年/月/日で、バックアップのバージョン識別子を指定します-HH:MM の形式です。 バージョン識別子がわからない場合は、 [wbadmin get versions](wbadmin-get-versions.md) コマンドを実行します。<p>システム状態の排他的なバックアップで構成されているバージョンは、このコマンドを使用して削除できます。 [Wbadmin get items](wbadmin-get-items.md)コマンドを実行して、バージョンの種類を表示します。 |
| -deleteOldest | 最も古いシステム状態のバックアップを削除します。 |
| -backuptarget | 削除するバックアップ用ストレージの場所を指定します。 ディスクバックアップの記憶域の場所には、ドライブ文字、マウントポイント、または GUID ベースのボリュームパスを指定できます。 この値は、ローカルコンピューター上にないバックアップを検索する場合にのみ指定する必要があります。 ローカルコンピューターのバックアップに関する情報は、ローカルコンピューター上のバックアップカタログで入手できます。 |
| -コンピューター | コンピューターを削除するがシステム状態のバックアップを指定します。 複数のコンピューターが同じ場所にバックアップされた場合に役立ちます。 ときに使用する必要があります、 **-backuptarget** パラメーターを指定します。 |
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

## <a name="examples"></a>使用例

2013 年 3 月 31 日の午前 10時 00分時に作成、システム状態バックアップを削除するには、次のように入力します。

```
wbadmin delete systemstatebackup -version:03/31/2013-10:00
```

最新の 3 つを除く、すべてのシステム状態バックアップを削除するには、次のように入力します。

```
wbadmin delete systemstatebackup -keepVersions:3
```

ディスク f: に格納されている最も古いシステム状態のバックアップを削除するには、次のように入力します。

```
wbadmin delete systemstatebackup -backupTarget:f:\ -deleteOldest
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [wbadmin get バージョンコマンド](wbadmin-get-versions.md)

- [wbadmin get items コマンド](wbadmin-get-items.md)
