---
title: set id
description: Diskpart の set id コマンドの参照記事。フォーカスのあるパーティションの [パーティションの種類] フィールドを変更します。
ms.topic: reference
ms.assetid: 5793d7ad-827e-4285-b2c6-ae60eeb0e886
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 0f25498a89cdb7347a40825af70621d5cd09440a
ms.sourcegitcommit: e164aeffc01069b8f1f3248bf106fcdb7f64f894
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/26/2020
ms.locfileid: "91389086"
---
# <a name="set-id-diskpart"></a>set id (Diskpart)

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

フォーカスのあるパーティションの [パーティションの種類] フィールドを変更します。 このコマンドは、ダイナミックディスクまたは Microsoft 予約パーティションでは機能しません。

> [!IMPORTANT]
> このコマンドは、相手先ブランド供給業者 (Oem) のみで使用することを目的としています。 このパラメーターを持つパーティションの種類フィールドを変更すると、エラーが発生したり、起動できなくなる、コンピューターが発生する可能性があります。 OEM または gpt ディスクの使用経験がない場合は、このパラメーターを使用して、gpt ディスク上のパーティションの種類のフィールドを変更しないでください。 代わりに、常に [create partition efi](create-partition-efi.md) コマンドを使用して efi システムパーティションを作成し、 [create partition msr](create-partition-msr.md) コマンドを使用して Microsoft 予約パーティションを作成します。また、ID パラメーターを指定せずに create partition [primary](create-partition-primary.md) コマンドを実行して、gpt ディスク上にプライマリパーティションを作成します。

## <a name="syntax"></a>構文

```
set id={ <byte> | <GUID> } [override] [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | [説明] |
|--|--|
| `<byte>` | マスターブートレコード (MBR) ディスクの場合、パーティションの type フィールドの新しい値を16進数形式で指定します。 パーティションの種類の **バイト** は、LDM パーティションを指定するタイプ0x42 を除き、このパラメーターで指定できます。 16進数のパーティションの種類を指定する場合は、先頭の0x が省略されていることに注意してください。 |
| `<GUID>` | GUID パーティションテーブル (gpt) ディスクの場合、パーティションの type フィールドに新しい GUID 値を指定します。 認識された Guid は次のとおりです。<ul><li>**EFI システムパーティション:** c12a7328-f81f-11d2-ba4b-00a0c93ec93b</li><li>**基本データパーティション:** ebd0a0a2-b9e5-4433-87c0-68b6b72699c7</li></ul>ただし、次は、このパラメーターでは、パーティションの種類の GUID を指定できます。<ul><li>**Microsoft 予約パーティション:** e3c9e316-0b5c-4db8-817d-f92df00215ae</li><li>**ダイナミックディスク上の LDM メタデータパーティション:** 5808c8aa-7e8f-42e0-85d2-e1e90434cfb3</li><li>**ダイナミックディスク上の LDM データパーティション:** af9b60a0-1431-4f62-bc68-3311714a69ad</li><li>**クラスターメタデータパーティション:** db97dba9-0840-4bae-97f0-ffb9a327c7e1</li></ul> |
| override | パーティションの種類を変更する前に、ボリューム上のファイルシステムのマウントを強制的に解除します。 **Set id**コマンドを実行すると、DiskPart によってボリューム上のファイルシステムのロックおよびマウント解除が試行されます。 **Override**が指定されておらず、ファイルシステムをロックする呼び出しが失敗した場合 (たとえば、開いているハンドルがあるため)、操作は失敗します。 **Override**が指定されている場合、ファイルシステムのロックの呼び出しが失敗した場合でも、DiskPart はマウントを強制的に解除し、ボリュームに対して開いているハンドルは有効でなくなります。 |
| noerr | スクリプト作成にのみ使用されます。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="remarks"></a>解説

- 前述の制限を超えると、DiskPart では、指定した値の有効性がチェックされません (16 進形式または GUID のバイトであることを確認する点が異なります)。

## <a name="examples"></a>例

Type フィールドを *0x07* に設定し、ファイルシステムのマウントを強制的に解除するには、次のように入力します。

```
set id=0x07 override
```

ベーシック データ パーティションにする型のフィールドを設定するには、次のように入力します。

```
set id=ebd0a0a2-b9e5-4433-87c0-68b6b72699c7
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)
