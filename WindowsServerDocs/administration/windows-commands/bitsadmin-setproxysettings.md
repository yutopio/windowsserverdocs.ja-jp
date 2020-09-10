---
title: bitsadmin setproxysettings
description: Bitsadmin setproxysettings コマンドの参照記事。指定されたジョブのプロキシ設定を設定します。
ms.topic: reference
ms.assetid: be8edb1b-614e-4d0b-a8f8-64b4bde3e64b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 199cb3f4b4259a52a8960cac23b9e408e71ded23
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630681"
---
# <a name="bitsadmin-setproxysettings"></a>bitsadmin setproxysettings

指定されたジョブのプロキシ設定を設定します。

## <a name="syntax"></a>構文

```
bitsadmin /setproxysettings <job> <usage> [list] [bypass]
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ----------- |
| ジョブ (job) | ジョブの表示名または GUID。 |
| usage | プロキシの使用方法を設定します。次に例を示します。<ul><li>**PRECONFIG.** 所有者の Internet Explorer の既定値を使用します。</li><li>**NO_PROXY。** プロキシサーバーは使用しないでください。</li><li>**オーバーライド.** 明示的なプロキシリストとバイパスリストを使用します。 プロキシの一覧とプロキシのバイパス情報は、の後に続く必要があります。</li><li>**認識.** プロキシ設定を自動的に検出します。</li></ul> |
| list | *Usage*パラメーターが OVERRIDE に設定されている場合に使用します。 使用するプロキシサーバーのコンマ区切りの一覧が含まれている必要があります。 |
| バイパス | *Usage*パラメーターが OVERRIDE に設定されている場合に使用します。 ホスト名または IP アドレスのスペース区切りの一覧、またはその両方を含める必要があります。この場合、転送はプロキシ経由でルーティングされません。 これは `<local>` 、同じ LAN 上のすべてのサーバーを参照することができます。 空のプロキシバイパスリストには NULL 値を使用できます。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブのさまざまな使用方法を使用してプロキシ設定を設定するには、次のようにします。

```
bitsadmin /setproxysettings myDownloadJob PRECONFIG
```

```
bitsadmin /setproxysettings myDownloadJob NO_PROXY
```
```
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1:80
```

```
bitsadmin /setproxysettings myDownloadJob OVERRIDE proxy1,proxy2,proxy3 NULL
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
