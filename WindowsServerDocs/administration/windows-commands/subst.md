---
title: subst
description: パスをドライブ文字に関連付ける方法について説明します。
ms.topic: reference
ms.assetid: 3e69234c-2312-4343-868b-afc1017c622a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: f5fd87c01f305201cfd9db50cd454da56bc99c53
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626855"
---
# <a name="subst"></a>subst



ドライブ文字をパスに関連付けます。 パラメーターを指定せずに使用する場合 **subst** 仮想ドライブの名前が有効で表示されます。



## <a name="syntax"></a>構文

```
subst [<Drive1>: [<Drive2>:]<Path>]
subst <Drive1>: /d
```

### <a name="parameters"></a>パラメーター

|パラメーター|Description|
|---------|-----------|
|\<Drive1>:|パスに割り当てる仮想ドライブを指定します。|
|[\<Drive2>:]\<Path>|物理ドライブと仮想ドライブに指定するパスを指定します。|
|/d|置き換えられた (仮想) ドライブを削除します。|
|/?|コマンド プロンプトにヘルプを表示します。|

## <a name="remarks"></a>注釈

-   次のコマンドは機能しません。 **subst** コマンドで指定されているドライブでは使用できません。

    **chkdsk**

    **diskcomp**

    **diskcopy**

    **format**

    **label**

    **recover**
-   *ドライブ 1* パラメーターがで指定された範囲内である必要があります、 **リソース** コマンドです。 ない場合は、 **subst** 次のエラー メッセージが表示されます。

    `Invalid parameter - drive1:`

## <a name="examples"></a><a name="BKMK_examples"></a>例

仮想ドライブ Z B:\User\Betty\Forms のパスを作成するには、次のように入力します。
```
subst z: b:\user\betty\forms
```
完全なパスを入力する代わりに次のように、コロンで後に仮想ドライブの文字を入力してこのディレクトリに移動することができます。
```
z:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)