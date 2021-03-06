---
title: load metadata
description: "\"メタデータの読み込み\" コマンドの参照記事。このコマンドは、転送可能なシャドウコピーをインポートする前にメタデータ .cab ファイルを読み込み、または復元の場合にライターメタデータを読み込みます。"
ms.topic: reference
ms.assetid: 2c535487-668b-44fc-babb-ff59cf7d190e
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 1d2895b4122d54de92dd595c5dc7218b5579acb6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89639538"
---
# <a name="load-metadata"></a>メタデータの読み込み

転送可能なシャドウコピーをインポートする前に、または復元の場合にライターメタデータを読み込む前に、メタデータ .cab ファイルを読み込みます。 パラメーターを指定せずに使用した場合、 **メタデータの読み込み** コマンドプロンプトでヘルプが表示されます。

## <a name="syntax"></a>構文

```
load metadata [<drive>:][<path>]<metadata.cab>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| `[<drive>:][<path>]` | メタデータファイルの場所を指定します。 |
| metadata.cab | 読み込むメタデータ .cab ファイルを指定します。 |

## <a name="remarks"></a>注釈

- **Import**コマンドを使用すると、**読み込みメタ**データによって指定されたメタデータに基づいて、転送可能なシャドウコピーをインポートできます。

- 復元用に選択したライターとコンポーネントを読み込むには、[ **復元の開始** ] コマンドの前にこのコマンドを実行する必要があります。

## <a name="examples"></a>例

既定の場所から metafile.cab という名前のメタデータファイルを読み込むには、次のように入力します。

```
load metadata metafile.cab
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [diskshadow コマンドのインポート](import.md)

- [restore コマンドの開始](begin-restore.md)
