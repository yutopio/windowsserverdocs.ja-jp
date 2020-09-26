---
title: select disk
description: ディスクの選択コマンドの参照記事。指定されたディスクを選択し、それにフォーカスを移動します。
ms.topic: reference
ms.assetid: a0da614b-09d9-433b-b4eb-9127f84431cb
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 194bd36305060c8adfec27435ef05bf87605b45c
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389245"
---
# <a name="select-disk"></a>select disk

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

指定されたディスクを選択し、それに、フォーカスを移動します。

## <a name="syntax"></a>構文

```
select disk={<n>|<disk path>|system|next}
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| `<n>` | フォーカスを受け取るディスクの数を指定します。 コンピューター上のすべてのディスク番号を表示するにを使用して、 **リスト ディスク** diskpart コマンドです。<p>**注**<br>複数のディスクを使用するシステムを構成する場合は、 **[ディスクの選択] = 0** を使用してシステムディスクを指定しないでください。 コンピューターは、コンピュータを再起動して、同じディスク構成を持つ別のコンピューターが別のディスク番号を持つ場合、ディスク番号を再割り当てできます。 |
| `<disk path>` | フォーカスを受け取るディスクの場所を指定します (例) `PCIROOT(0)#PCI(0F02)#atA(C00T00L00)` 。 ディスクの場所のパスを表示するには、それを選択し、入力 **詳細ディスク**します。 |
| システム | BIOS コンピューターでは、このオプションはディスク0がフォーカスを受け取ることを指定します。 EFI コンピューターでは、現在のブートに使用される EFI システムパーティション (ESP) を含むディスクがフォーカスを受け取ります。 EFI コンピューターでは、ESP がない場合、または ESP が複数ある場合、またはコンピューターが Windows プレインストール環境 (Windows PE) から起動された場合、コマンドは失敗します。 |
| [次へ] | ディスクを選択すると、このオプションにより、ディスクの一覧にあるすべてのディスクが反復処理されます。 このオプションを実行すると、一覧の次のディスクがフォーカスを受け取ります。 |

## <a name="examples"></a>例

ディスク 1 にフォーカスを切り替えるには、次のように入力します。

```
select disk=1
```

ディスクを選択して、その場所のパスを使用して、次のように入力します。

```
select disk=PCIROOT(0)#PCI(0100)#atA(C00T00L01)
```

システム ディスクにフォーカスを次のように入力します。

```
select disk=system
```

フォーカスを次のディスクをコンピューターに、次のように入力します。

```
select disk=next
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [パーティションの選択コマンド](select-partition.md)

- [vdisk コマンドを選択する](select-vdisk.md)

- [ボリュームの選択コマンド](select-volume.md)
