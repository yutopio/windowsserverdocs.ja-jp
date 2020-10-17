---
title: vssadmin resize shadowstorage
description: Vssadmin resize shadowstorage コマンドの説明。これは、シャドウコピー記憶域に使用できる記憶域の最大容量のサイズを変更します。
ms.topic: reference
author: JasonGerend
ms.author: jgerend
ms.date: 03/05/2020
ms.localizationpriority: medium
ms.openlocfilehash: 704130890d68c271e74a9163ba4ae76dcfb1a516
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156143"
---
# <a name="vssadmin-resize-shadowstorage"></a>vssadmin resize shadowstorage

> 適用対象: Windows 10、Windows 8.1、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012、Windows Server 2008 R2、Windows Server 2008

シャドウコピーの記憶域に使用できる記憶域の最大容量のサイズを変更します。

シャドウコピー記憶域に使用できる記憶域の最小容量は、 **Mindiffgram** のレジストリ値を使用して指定できます。 詳細については、「 [Mindiffgram](/windows/win32/backup/registry-keys-for-backup-and-restore#mindiffareafilesize)」を参照してください。

> [!WARNING]
> 記憶域の関連付けのサイズを変更すると、シャドウコピーが消失する可能性があります。

## <a name="syntax"></a>構文

```
vssadmin resize shadowstorage /for=<ForVolumeSpec> /on=<OnVolumeSpec> [/maxsize=<MaxSizeSpec>]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /for =`<ForVolumeSpec>` | ストレージ領域の最大サイズを変更するボリュームを指定します。 |
| /on =`<OnVolumeSpec>` | 記憶域ボリュームを指定します。 |
| [/maxsize = `<MaxSizeSpec>` ] | シャドウコピーの格納に使用できる領域の最大サイズを指定します。 **/Maxsize**に値が指定されていない場合、使用できるストレージ領域の量に制限はありません。<p>**MaxSizeSpec**値は 1 MB 以上である必要があり、KB、MB、GB、TB、PB、EB のいずれかの単位で表す必要があります。 単位が指定されていない場合、 **MaxSizeSpec** は既定でバイトを使用します。 |

## <a name="examples"></a>使用例

ボリューム D のボリューム C のシャドウコピーのサイズを変更するには (最大サイズは 900MB)、次のように入力します。

```
vssadmin resize shadowstorage /For=C: /On=D: /MaxSize=900MB
```

ボリューム D のボリューム C のシャドウコピーのサイズを変更するには、最大サイズを使用せずに、次のように入力します。

```
vssadmin resize shadowstorage /For=C: /On=D: /MaxSize=UNBOUNDED
```

ボリューム C のシャドウコピーのサイズを20% に変更するには、次のように入力します。

```
vssadmin resize shadowstorage /For=C: /On=C: /MaxSize=20%
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [vssadmin コマンド](vssadmin.md)
