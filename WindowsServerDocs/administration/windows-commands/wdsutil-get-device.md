---
title: wdsutil get-デバイス
description: Wdsutil get device のリファレンス記事。事前登録されたコンピューター (つまり、active directory ドメインサービスのコンピューターアカウントに適用された物理コンピューター) に関する Windows 展開サービス情報を取得します。
ms.topic: reference
ms.assetid: 1da79286-7e1d-45f2-aea2-d446e16a6911
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: 875ab5053ebbb1708f7b51896c9d82b9eba8f725
ms.sourcegitcommit: 720455aad2bac78cf64997d196a13f35ea0acb73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/05/2020
ms.locfileid: "91730842"
---
# <a name="wdsutil-get-device"></a>wdsutil get-デバイス

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

事前設定されたコンピューター (つまり、active directory ドメインサービスのコンピューターアカウントに関連する物理コンピューター) に関する Windows 展開サービス情報を取得します。

## <a name="syntax"></a>構文
```
wdsutil /Get-Device {/Device:<Device name> | /ID:<MAC or UUID>} [/Domain:<Domain>] [/forest:{Yes | No}]
```
### <a name="parameters"></a>パラメーター
|パラメーター|説明|
|-------|--------|
|ドライブ<Device name>|コンピューター (SAMAccountName) の名前を指定します。|
|番号<MAC or UUID>|次の例に示すように、MAC アドレスまたはコンピューターの UUID (GUID) のいずれかを指定します。 有効な GUID は、バイナリ文字列または GUID 文字列の2つの形式のいずれかにする必要があります。<p>-   **バイナリ文字列**:/ID: ACEFA3E81F20694E953EB2DAA1E8B1B6<br />-   **MAC アドレス**: 00B056882FDC (ダッシュなし) または 00-B0-56-88-2F-DC (ダッシュ付き)<br />-   **GUID 文字列**:/ID: E8A3EFAC-4E69-953-B2DAA1E8B1B6|
|[/ドメイン:<Domain>]|事前登録されたコンピューターを検索するドメインを指定します。 このパラメーターの既定値は、ローカル ドメインです。|
|[/forest: {Yes &#124; No}]|Windows 展開サービスがフォレスト全体またはローカル ドメインを検索する必要があるかどうかを指定します。 既定値は **いいえ**, 、ローカルのドメインのみを検索することを意味します。|
## <a name="examples"></a>例
情報を取得するコンピューター名を使用して、次のように入力します。
```
wdsutil /Get-Device /Device:computer1
```
情報を取得する MAC アドレスを使用して、次のように入力します。
```
wdsutil /verbose /Get-Device /ID:00-B0-56-88-2F-DC /Domain:MyDomain
```
情報を取得する GUID 文字列を使用して、次のように入力します。
```
wdsutil /verbose /Get-Device /ID:E8A3EFAC-201F-4E69-953-B2DAA1E8B1B6 /forest:Yes
```
## <a name="additional-references"></a>その他のリファレンス
- [コマンド ライン構文の記号](command-line-syntax-key.md)
- [wdsutil set-デバイスコマンド](wdsutil-set-device.md)
- [wdsutil デバイスの追加コマンド](wdsutil-add-device.md)
- [wdsutil get-alldevices コマンド](wdsutil-get-alldevices.md)
