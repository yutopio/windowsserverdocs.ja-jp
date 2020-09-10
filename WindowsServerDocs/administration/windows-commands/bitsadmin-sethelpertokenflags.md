---
title: bitsadmin sethelpertokenflags
description: Bitsadmin se pertokenflags コマンドのリファレンス記事。 BITS 転送ジョブに関連付けられているヘルパートークンの使用フラグを設定します。
ms.topic: reference
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 03/01/2019
ms.openlocfilehash: 23a2626fcd1eb92c388ea1dc24682526bac59af5
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630886"
---
# <a name="bitsadmin-sethelpertokenflags"></a>bitsadmin sethelpertokenflags

BITS 転送ジョブに関連付けられている [ヘルパートークン](/windows/win32/bits/helper-tokens-for-bits-transfer-jobs)の使用フラグを設定し   ます。

> [!NOTE]
> このコマンドは、BITS 3.0 以前ではサポートされていません。

## <a name="syntax"></a>構文

```
bitsadmin /sethelpertokenflags <job> <flags>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| flags | 次のようなヘルパートークン値を使用できます。<ul><li>**0x0001.** アップロードジョブのローカルファイルを開き、ダウンロードジョブの一時ファイルを作成または名前変更するため、またはアップロード/応答ジョブの応答ファイルを作成または名前を変更するために使用します。</li><li>**0x0002.** サーバーメッセージブロック (SMB) のアップロードジョブまたはダウンロードジョブのリモートファイルを開くため、または暗黙の NTLM または Kerberos 資格情報に対する HTTP サーバーまたはプロキシチャレンジに対する応答として使用されます。</li></ul> `/setcredentialsjob targetscheme null null`   HTTP 経由で資格情報を送信するには、を呼び出す必要があります。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
