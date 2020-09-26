---
title: select volume
description: ボリュームの選択コマンドの参照記事。指定されたボリュームを選択し、それにフォーカスを移動します。
ms.topic: reference
ms.assetid: 5d70d776-80ad-4f20-8288-a7997fb1df28
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 643db6484842e8a67462b0460a1ecdeac653e577
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389190"
---
# <a name="select-volume"></a>select volume

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定されたボリュームを選択し、それに、フォーカスを移動します。 このコマンドは、選択したディスクにフォーカスが置かれているボリュームを表示することもできます。

## <a name="syntax"></a>構文

```
select volume={<n>|<d>}
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| `<n>` | フォーカスを受け取るボリュームの数。 使用して現在選択されているディスク上のすべてのボリュームの番号を表示する、 **ボリュームを一覧表示** diskpart コマンドです。 |
| `<d> `| フォーカスを受け取るボリュームのドライブ文字またはマウント ポイントのパス。 |

## <a name="remarks"></a>解説

- ボリュームが指定されていない場合、このコマンドは、選択したディスクにフォーカスが置かれているボリュームを表示します。

- ベーシック ディスクにボリュームを選択するともにフォーカスを対応するパーティション。

  - 対応するパーティションを持つボリュームを選択したパーティションが自動的に選択します。

  - パーティションが対応するボリュームで選択されている場合、ボリュームを自動的に選択されます。

## <a name="examples"></a>例

*ボリューム 2*にフォーカスを移動するには、次のように入力します。

```
select volume=2
```

フォーカスを *ドライブ C*に移動するには、次のように入力します。

```
select volume=c
```

*C:\mountpath*という名前のフォルダーにマウントされているボリュームにフォーカスを移動するには、次のように入力します。

```
select volume=c:\mountpath
```

選択したディスクにフォーカスが置かれているボリュームを表示するには、次のように入力します。

```
select volume
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ボリュームの追加コマンド](add-volume.md)

- [attributes volume コマンド](attributes-volume.md)

- [ボリュームミラーの作成コマンド](create-volume-mirror.md)

- [ボリューム raid の作成コマンド](create-volume-raid.md)

- [create volume simple コマンド](create-volume-simple.md)

- [ボリュームストライプの作成コマンド](create-volume-stripe.md)

- [ボリュームの削除コマンド](delete-volume.md)

- [詳細ボリュームコマンド](detail-volume.md)

- [fsutil volume コマンド](fsutil-volume.md)

- [ボリュームの一覧表示コマンド](list-volume.md)

- [offline volume コマンド](offline-volume.md)

- [onine ボリュームコマンド](online-volume.md)

- [ディスクの選択コマンド](select-disk.md)

- [パーティションの選択コマンド](select-partition.md)

- [vdisk コマンドを選択する](select-vdisk.md)
