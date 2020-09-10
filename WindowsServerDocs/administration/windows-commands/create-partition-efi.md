---
title: create partition efi
description: Create partition efi コマンドのリファレンス記事では、Itanium ベースのコンピューター上の GUID パーティションテーブル (gpt) ディスクに拡張ファームウェアインターフェイス (EFI) システムパーティションを作成します。
ms.topic: reference
ms.assetid: 3cfc1fca-6515-4a4d-bfae-615fa8045ea9
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a3eacad949a4a5c14c40da0469155e277cb274b6
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89629205"
---
# <a name="create-partition-efi"></a>create partition efi

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

Itanium ベースのコンピューター上の GUID パーティションテーブル (gpt) ディスクに、拡張ファームウェアインターフェイス (EFI) システムパーティションを作成します。 パーティションが作成されると、新しいパーティションにフォーカスが割り当てられます。

>[!NOTE]
> この操作を成功させるには、gpt ディスクを選択する必要があります。 使用して、 [select ディスク](select-disk.md) コマンド ディスクを選択し、それにフォーカスをします。

## <a name="syntax"></a>構文

```
create partition efi [size=<n>] [offset=<n>] [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| サイズ =`<n>` | パーティションのサイズ (mb)。 サイズが指定されていない場合は、現在の領域に空き領域がなくなるまで、パーティションは続行されます。 |
| オフセット =`<n>` | パーティションが作成されるオフセット (kb 単位)。 オフセットが指定されていない場合、パーティションは、それを保持するのに十分な大きさの最初のディスクエクステントに配置されます。 |
| noerr | スクリプト専用です。 エラーが発生しても、エラーが発生しなかったかのように DiskPart はコマンドの処理を続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

#### <a name="remarks"></a>注釈

- **Create**コマンドを使用する前に、[**ボリュームの追加**] コマンドでボリュームを少なくとも1つ追加する必要があります。

- **Create**コマンドを実行した後、 **exec**コマンドを使用して、シャドウコピーからバックアップ用の複製スクリプトを実行できます。

- [ **バックアップの開始** ] コマンドを使用すると、コピーバックアップではなく完全バックアップを指定できます。

## <a name="examples"></a>例

選択したディスクに 1000 mb の EFI パーティションを作成するには、次のように入力します。

```
create partition efi size=1000
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [create コマンド](create.md)

- [select disk](select-disk.md)
