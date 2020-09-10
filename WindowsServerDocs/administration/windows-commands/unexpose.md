---
title: unexpose
description: '[公開] コマンドを使用して公開されたシャドウコピーを公開しない、非公開の参照記事。'
ms.topic: reference
ms.assetid: 58dc7d0f-52e9-4587-9487-d3b4c3e52640
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 76e1666bd87a3304dcbe8de3025a0ec790cf83d7
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89626583"
---
# <a name="unexpose"></a>unexpose

[ **公開** ] コマンドを使用して公開されたシャドウコピーを公開しません。 公開されたシャドウコピーは、シャドウ ID、ドライブ文字、共有、またはマウントポイントによって指定できます。



## <a name="syntax"></a>構文

```
unexpose {<ShadowID> | <Drive:> | <Share> | <MountPoint>}
```

### <a name="parameters"></a>パラメーター

|パラメーター|Description|
|---------|-----------|
|\<ShadowID>|指定したシャドウ ID によって指定されたシャドウコピーを非公開にします。|
|\<Drive:>|指定したドライブ文字 (ドライブ P など) に関連付けられているシャドウコピーを非公開にします。|
|\<Share>|指定した共有に関連付けられているシャドウコピーを非表示に \\ \\ します ( *MachineName*など) \) 。|
|\<MountPoint>|指定されたマウントポイントに関連付けられているシャドウコピーを非公開にします (例、C:\ シャドウコピー \) 。|

## <a name="remarks"></a>注釈

-   *ShadowID*の代わりに、既存のエイリアスまたは環境変数を使用できます。 既存のエイリアスを表示するには、パラメーターを指定せずに **add** を使用します。

## <a name="examples"></a>例

ドライブ P に関連付けられたシャドウコピーを公開しないようにするには、次のように入力します。
```
unexpose P:
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)