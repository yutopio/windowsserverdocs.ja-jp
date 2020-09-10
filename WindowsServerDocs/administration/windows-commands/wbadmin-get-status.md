---
title: wbadmin get status
description: 現在実行中のバックアップまたは回復操作の状態を報告する wbadmin get status の参照記事。
ms.topic: reference
ms.assetid: 2911b944-7b95-46aa-8c1e-1d55a2fcc94c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 7dcb1b59de6827500311cfd55245ac6c94a171b0
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624595"
---
# <a name="wbadmin-get-status"></a>wbadmin get status



現在実行中のバックアップまたは回復操作の状態を報告します。

このサブコマンドを使用するには、 **Backup Operators** グループまたは **Administrators** グループのメンバであるか、適切な権限が委任されている必要があります。 さらに、実行する必要があります **wbadmin** 管理者特権でコマンド プロンプトからです。 (管理者特権でのコマンドプロンプトを開くには、[ **コマンドプロンプト**] を右クリックし、[ **管理者として実行**] をクリックします)。

## <a name="syntax"></a>構文

```
wbadmin get status
```

### <a name="parameters"></a>パラメーター

このサブコマンドにはパラメーターがありません。

## <a name="remarks"></a>注釈

-   このサブコマンドは、現在のバックアップまたは回復操作が完了するまで停止しません。コマンドウィンドウを閉じた場合でも、サブコマンドは引き続き実行されます。
-   現在のバックアップまたは回復操作を停止する場合は、 **wbadmin stop job** サブコマンドを使用します。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   [WBJob](/powershell/module/windowserverbackup/?view=winserver2012r2-ps) コマンドレット
