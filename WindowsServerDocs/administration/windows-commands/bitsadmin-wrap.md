---
title: bitsadmin wrap
description: Bitsadmin wrap コマンドの参照記事。コマンドウィンドウの右端から次の行まで拡張する出力テキストの行をラップします。
ms.topic: reference
ms.assetid: 14e57522-539d-4621-ad15-09f7a44ccab7
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 24fa50e153d52ec74ab728a132aadd1b95c7a9da
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89630380"
---
# <a name="bitsadmin-wrap"></a>bitsadmin wrap

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

コマンドウィンドウの右端から次の行まで拡張する出力テキストの行をラップします。 このスイッチは、他のスイッチの前に指定する必要があります。

既定では、 [bitsadmin monitor](bitsadmin-monitor.md) スイッチを除くすべてのスイッチによって出力テキストがラップされます。

## <a name="syntax"></a>構文

```
bitsadmin /wrap <job>
```

### <a name="parameters"></a>パラメーター

| パラメーター | Description |
| --------- | ---------- |
| ジョブ (job) | ジョブの表示名または GUID。 |

## <a name="examples"></a>例

*Mydownloadjob*という名前のジョブの情報を取得し、出力テキストをラップするには、次のように入力します。

```
bitsadmin /wrap /info myDownloadJob /verbose
```

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [bitsadmin コマンド](bitsadmin.md)
