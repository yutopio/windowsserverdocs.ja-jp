---
title: bitsadmin gethelpertokenflags
description: BITS 転送ジョブに関連付けられているヘルパートークンの使用フラグを返す、bitsadmin geの pertokenflags コマンドの参照記事。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 244dee15e201c877bdf3c17a219e190bee9a5821
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89632055"
---
# <a name="bitsadmin-gethelpertokenflags"></a>bitsadmin gethelpertokenflags

BITS 転送ジョブに関連付けられている [ヘルパートークン](/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)の使用フラグを返し   ます。

> [!NOTE]
> このコマンドは、BITS 3.0 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /gethelpertokenflags <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| -------------- | -------------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

### <a name="remarks"></a>注釈

次のような戻り値が返される可能性があります。

- **0x0001.** ヘルパートークンは、アップロードジョブのローカルファイルを開き、ダウンロードジョブの一時ファイルを作成または名前を変更するため、またはアップロード/応答ジョブの応答ファイルを作成または名前を変更するために使用されます。

- **0x0002.** ヘルパートークンは、サーバーメッセージブロック (SMB) のアップロードジョブまたはダウンロードジョブのリモートファイルを開くため、または暗黙の NTLM または Kerberos 資格情報に対する HTTP サーバーまたはプロキシのチャレンジに対する応答として使用されます。  `/SetCredentialsJob TargetScheme NULL NULL`   資格情報が HTTP 経由で送信されるようにするには、を呼び出す必要があります。

## <a name="examples"></a>例

*Mydownloadjob*という名前の BITS 転送ジョブに関連付けられているヘルパートークンの使用フラグを取得するには、次のようにします。

```
bitsadmin /gethelpertokenflags myDownloadJob
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
