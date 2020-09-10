---
title: wbadmin delete catalog
description: Wbadmin delete catalog の参照記事。ローカルコンピューターに格納されているバックアップカタログを削除します。
ms.topic: reference
ms.assetid: d3041407-4577-4716-a39f-2c8ab48818d1
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 64b5664ffeb676bf63ece83bd419f154cb96bb20
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89637885"
---
# <a name="wbadmin-delete-catalog"></a>wbadmin delete catalog



ローカル コンピューターに格納されているバックアップ カタログを削除します。 このコマンドを使用してバックアップ カタログが壊れているを使用してそれを復元することはできませんと **wbadmin restore catalog**します。

このサブコマンドでバックアップ カタログを削除するには、メンバーである、 **バックアップ オペレーター** グループ、または **管理者** グループ、またはをされている必要が適切なアクセス許可を委任します。 さらに、実行する必要があります **wbadmin** 管理者特権でコマンド プロンプトからです。 (管理者特権でのコマンドプロンプトを開くには、[ **コマンドプロンプト**] を右クリックし、[ **管理者として実行**] をクリックします)。

## <a name="syntax"></a>構文

```
wbadmin delete catalog
[-quiet]
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------|-----------|
|-quiet|ユーザーにプロンプトを表示せずにサブコマンドを実行します。|

## <a name="remarks"></a>注釈

コンピューターのバックアップ カタログを削除した場合の Windows Server バックアップ スナップインを使用してそのコンピューターで作成されたバックアップにアクセスすることができなきます。 この場合、別のバックアップ場所にアクセスする場合は、使用 **wbadmin restore catalog** をその場所からカタログのバックアップを復元します。 バックアップ カタログを削除した後は、新しいバックアップを作成する必要があります。

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)
-   [Wbadmin](wbadmin.md)
-   [削除 WBCatalog](/powershell/module/windowserverbackup/?view=winserver2012r2-ps)
