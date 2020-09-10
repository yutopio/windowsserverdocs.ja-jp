---
title: Verbose コマンドの使用
description: 詳細については、指定されたコマンドの詳細な出力を表示するリファレンス記事を参照してください。
ms.topic: reference
ms.assetid: fcf30ae7-818f-4e7e-a083-a1812682032b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: a5c05590bbbb3f1b185a64d6b0081a3d230d6b41
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89640456"
---
# <a name="using-the-verbose-command"></a>Verbose コマンドの使用

指定したコマンドの詳細な出力が表示されます。 使用することができます **/verbose** を実行するその他の WDSUTIL コマンドを使用します。 指定する必要があります **/verbose** と **]、[進行状況の** 直後後 **WDSUTIL**します。

## <a name="syntax"></a>構文

```
WDSUTIL /verbose <commands>
```

## <a name="examples"></a>例

自動追加データベースから承認済みのコンピュータを削除し、詳細な出力を表示する、次のように入力します。

```
WDSUTIL /Verbose /progress /Delete-AutoAddDevices /Server:MyWDSServer /DeviceType:ApprovedDevices
```