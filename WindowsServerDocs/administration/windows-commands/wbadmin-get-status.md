---
title: wbadmin get status
description: Wbadmin get status コマンドの参照記事。現在実行中のバックアップまたは回復操作の状態を報告します。
ms.topic: reference
ms.assetid: 2911b944-7b95-46aa-8c1e-1d55a2fcc94c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 764c5d3dc808b12488e36af5808acf4c895c5af1
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92155947"
---
# <a name="wbadmin-get-status"></a>wbadmin get status

現在実行中のバックアップまたは回復操作の状態を報告します。

このコマンドを使用して現在実行中のバックアップまたは回復操作の状態を取得するには、 **Backup Operators** グループまたは **Administrators** グループのメンバーであるか、適切なアクセス許可が委任されている必要があります。 さらに、**コマンドプロンプト**を右クリックし、[**管理者として実行**] を選択して、管理者特権でのコマンドプロンプトから**wbadmin**を実行する必要があります。

> [!IMPORTANT]
> このコマンドは、バックアップまたは回復操作が完了するまで停止しません。 コマンドウィンドウを閉じても、コマンドは引き続き実行されます。 現在のバックアップまたは回復操作を停止するには、 [wbadmin stop job](wbadmin-stop-job.md) コマンドを実行します。

## <a name="syntax"></a>構文

```
wbadmin get status
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [wbadmin コマンド](wbadmin.md)

- [wbadmin stop ジョブコマンド](wbadmin-stop-job.md)

- [WBJob](/powershell/module/windowserverbackup/Get-WBJob)
