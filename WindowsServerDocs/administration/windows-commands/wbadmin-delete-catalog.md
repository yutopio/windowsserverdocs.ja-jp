---
title: wbadmin delete catalog
description: Wbadmin delete catalog コマンドの参照記事。ローカルコンピューターに格納されているバックアップカタログを削除します。
ms.topic: reference
ms.assetid: d3041407-4577-4716-a39f-2c8ab48818d1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 4a19d856b65fdcf17fb369d81607445530f77275
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156100"
---
# <a name="wbadmin-delete-catalog"></a>wbadmin delete catalog

ローカル コンピューターに格納されているバックアップ カタログを削除します。 このコマンドは、バックアップカタログが破損していて、 [wbadmin restore catalog](wbadmin-restore-catalog.md) コマンドを使用して復元できない場合に使用します。

このコマンドを使用してバックアップカタログを削除するには、 **Backup Operators** グループまたは **Administrators** グループのメンバであるか、適切な権限が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

## <a name="syntax"></a>構文

```
wbadmin delete catalog [-quiet]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| -quiet | ユーザーにプロンプトを表示せずにコマンドを実行します。 |

#### <a name="remarks"></a>解説

- コンピューターのバックアップカタログを削除すると、Windows Server バックアップスナップインを使用してそのコンピューターに対して作成されたバックアップを取得できなくなります。 ただし、別のバックアップの場所にアクセスして [wbadmin restore catalog](wbadmin-restore-catalog.md) コマンドを実行できる場合は、その場所からバックアップカタログを復元できます。

- バックアップカタログを削除した後に、新しいバックアップを作成することを強くお勧めします。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [wbadmin restore catalog コマンド](wbadmin-restore-catalog.md)

- [削除 WBCatalog](/powershell/module/windowsserverbackup/Remove-WBCatalog)
