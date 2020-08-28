---
title: Progress コマンドの使用
description: 進行状況に関する参照記事。コマンドの実行中に進行状況を表示します。
ms.topic: reference
ms.assetid: 8ce5e77b-e13f-4ac3-948d-31770a6c7e25
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 33e0494133523748b599ab9e3673d4f786e044df
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89038310"
---
# <a name="using-the-progress-command"></a>Progress コマンドの使用

コマンドの実行中に進行状況を表示します。 使用することができます **]、[進行状況の** を実行するその他の WDSUTIL コマンドを使用します。 指定する必要があります **/verbose** と **]、[進行状況の** 直後後 **WDSUTIL**します。

## <a name="syntax"></a>構文

```
WDSUTIL /progress <commands>
```

## <a name="examples"></a>例

サーバーを初期化して進行状況を表示、次のように入力します。
```
WDSUTIL /Verbose /Progress /Initialize-Server /Server:MyWDSServer /RemInst:C:\RemoteInstall
```