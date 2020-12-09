---
title: mqbkup
description: Mqbkup コマンドの参照記事。これは、MSMQ メッセージファイルとレジストリ設定をストレージデバイスにバックアップし、以前に保存されたメッセージと設定を復元します。
ms.topic: reference
ms.assetid: 7bdd41c4-75ef-455f-b241-1d64a4c7acf5
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 90eabbcaa878f65a6df087d6eaeded6c279eb039
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96865011"
---
# <a name="mqbkup"></a>mqbkup

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

MSMQ メッセージファイルとレジストリ設定をストレージデバイスにバックアップし、以前に保存されたメッセージと設定を復元します。

バックアップと復元の両方の操作によって、ローカルの MSMQ サービスが停止されます。 MSMQ サービスが事前に開始されている場合、ユーティリティは、バックアップまたは復元操作の最後に MSMQ サービスの再起動を試みます。 ユーティリティを実行する前にサービスが既に停止していた場合、サービスの再起動は行われません。

MSMQ メッセージのバックアップ/復元ユーティリティを使用する前に、MSMQ を使用しているすべてのローカルアプリケーションを閉じる必要があります。

## <a name="syntax"></a>構文

```
mqbkup {/b | /r} <folder path_to_storage_device>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ------- | -------- |
| /b | バックアップ操作を指定します。 |
| /r | 復元操作を指定します。 |
| `<folder path_to_storage_device>` | MSMQ メッセージファイルとレジストリ設定が格納されるパスを指定します。 |
| /? | コマンド プロンプトにヘルプを表示します。 |

#### <a name="remarks"></a>注釈

- バックアップ操作または復元操作の実行中に指定されたフォルダーが存在しない場合、そのフォルダーはユーティリティによって自動的に作成されます。

- 既存のフォルダーを指定する場合は、空にする必要があります。 空ではないフォルダーを指定すると、ユーティリティは、その中に含まれるすべてのファイルとサブフォルダーを削除します。 この場合、既存のファイルとサブフォルダーを削除する権限を付与するように求められます。 **/Y** パラメーターを使用して、指定したフォルダー内の既存のすべてのファイルとサブフォルダーの削除に対して事前に同意したことを示すことができます。

- MSMQ メッセージファイルの格納に使用されるフォルダーの場所は、レジストリに格納されます。 このため、ユーティリティは、復元操作の前に使用されていたストレージフォルダーではなく、レジストリで指定されているフォルダーに MSMQ メッセージファイルを復元します。

### <a name="examples"></a>例

すべての MSMQ メッセージファイルとレジストリ設定をバックアップし、C: ドライブの *msmqbkup* フォルダーに保存するには、次のように入力します。

```
mqbkup /b c:\msmqbkup
```

C: ドライブの *oldbkup* フォルダーにある既存のすべてのファイルとサブフォルダーを削除し、MSMQ メッセージファイルとレジストリ設定をフォルダーに格納するには、次のように入力します。

```
mqbkup /b /y c:\oldbkup
```

MSMQ メッセージとレジストリ設定を復元するには、次のように入力します。

```
mqbkup /r c:\msmqbkup
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [MSMQ Powershell リファレンス](/powershell/module/msmq/)
