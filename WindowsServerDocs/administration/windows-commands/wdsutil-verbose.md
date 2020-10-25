---
title: Verbose コマンドの使用
description: 詳細については、指定されたコマンドの詳細な出力を表示するリファレンス記事を参照してください。
ms.topic: reference
ms.assetid: fcf30ae7-818f-4e7e-a083-a1812682032b
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 2335ef8bf3e3b231851d424f99f0a7e878218c4b
ms.sourcegitcommit: 554d274fea48a4d47c19845d969a9ec93dec82de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92524877"
---
# <a name="using-the-verbose-command"></a>Verbose コマンドの使用

指定したコマンドの詳細な出力が表示されます。 **/Verbose**は、実行するその他の wdsutil コマンドと共に使用できます。 **Wdsutil**と **/progress**は **、** wdsutil の直後に指定する必要があることに注意してください。

## <a name="syntax"></a>構文

```
wdsutil /verbose <commands>
```

## <a name="examples"></a>例

自動追加データベースから承認済みのコンピュータを削除し、詳細な出力を表示する、次のように入力します。

```
wdsutil /Verbose /progress /Delete-AutoAddDevices /Server:MyWDSServer /DeviceType:ApprovedDevices
```