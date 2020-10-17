---
title: uniqueid
description: フォーカスがあるディスクの GUID パーティションテーブル (GPT) 識別子またはマスターブートレコード (MBR) 署名を表示または設定する uniqueid の参照記事。
ms.topic: reference
ms.assetid: 64235a4a-b91c-46da-b9b0-68ee90571c2a
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 73721316747ffd0380f178622d37dc4fdbefc2fb
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156299"
---
# <a name="uniqueid"></a>uniqueid

フォーカスがあるベーシックディスクまたはダイナミックディスクの GUID パーティションテーブル (GPT) 識別子またはマスターブートレコード (MBR) 署名を表示または設定します。 この操作を成功させるには、ベーシックディスクまたはダイナミックディスクを選択する必要があります。 [[ディスクの選択] コマンド](select-disk.md)を使用してディスクを選択し、それにフォーカスを移動します。

## <a name="syntax"></a>構文

```
uniqueid disk [id={<dword> | <GUID>}] [noerr]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| id =`{<dword> | <GUID>}` | MBR ディスクの場合、このパラメーターは、16進数形式の4バイト (DWORD) 値を署名に指定します。 GPT ディスクの場合、このパラメーターは識別子の GUID を指定します。 |
| noerr | スクリプト専用です。 エラーが発生した場合、DiskPart はエラーが発生しなかったかのようにコマンドを処理し続けます。 このパラメーターは、エラー発生すると、DiskPart はエラー コードを生成して終了します。 |

## <a name="examples"></a>使用例

フォーカスがある MBR ディスクの署名を表示するには、次のように入力します。

```
uniqueid disk
```

フォーカスがある MBR ディスクの署名を DWORD 値 *5f1b2c36*に設定するには、次のように入力します。

```
uniqueid disk id=5f1b2c36
```

フォーカスがある GPT ディスクの識別子を GUID 値 baf784e7-6bbd-4cfb-aaac-e86c96e166ee に設定するには、次のように入力します。

```
uniqueid disk id=baf784e7-6bbd-4cfb-aaac-e86c96e166ee
```

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ディスクの選択コマンド](select-disk.md)
