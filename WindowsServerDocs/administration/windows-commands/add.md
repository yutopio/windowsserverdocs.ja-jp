---
title: add
description: '[追加] コマンドの参照記事。シャドウコピーするボリュームのセットにボリュームを追加するか、エイリアス環境にエイリアスを追加します。'
ms.topic: reference
ms.assetid: 47efce7a-86d2-4872-ae31-baa108757afd
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: ddd090323b45caa0cc7afa4c07c568793f2e268d
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89633494"
---
# <a name="add"></a>add

シャドウコピーするボリュームのセットにボリュームを追加するか、エイリアス環境に別名を追加します。 サブコマンドなしで使用する場合は、現在のボリュームとエイリアスの一覧を **追加** します。

> [!NOTE]
> エイリアスは、シャドウコピーが作成されるまでエイリアス環境に追加されません。 すぐに必要なエイリアスを追加するには、 **add alias**を使用します。

## <a name="syntax"></a>構文

```
add
add volume <volume> [provider <providerid>]
add alias <aliasname> <aliasvalue>
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| ---------- | ----------- |
| ボリューム | シャドウコピーするボリュームのセットであるボリュームをシャドウコピーセットに追加します。 「構文とパラメーターの [ボリュームの追加](add-volume.md) 」を参照してください。 |
| alias | 指定された名前と値をエイリアス環境に追加します。 「構文とパラメーターの [別名の追加](add-alias.md) 」を参照してください。 |
| /? | コマンドラインでヘルプを表示します。 |

## <a name="examples"></a>例

追加されたボリュームと現在の環境内にある別名を表示するには、次のように入力します。

```
add
```

次の出力は、ドライブ C がシャドウコピーセットに追加されたことを示しています。

```
Volume c: alias System1    GUID \\?\Volume{XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX}\
1 volume in Shadow Copy Set.
No Diskshadow aliases in the environment.
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)