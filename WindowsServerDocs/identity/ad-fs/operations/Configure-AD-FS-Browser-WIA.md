---
title: AD FS で Windows 統合認証 (WIA) を使用するようにブラウザーを構成する
description: このドキュメントでは、AD FS で WIA を使用するようにブラウザーを構成する方法について説明します
author: billmath
ms.author: billmath
manager: femila
ms.date: 03/20/2020
ms.topic: article
ms.openlocfilehash: 61369f2dde82264190bcbd4d81eaae317e159a0d
ms.sourcegitcommit: 7c0794e257f602bd71af5eb9a11b8a03d2b9adfd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/14/2020
ms.locfileid: "97390270"
---
# <a name="configure-browsers-to-use-windows-integrated-authentication-wia-with-ad-fs"></a>AD FS で Windows 統合認証 (WIA) を使用するようにブラウザーを構成する

既定では、windows 統合認証 (WIA) は、認証にブラウザーを使用する任意のアプリケーションの組織の内部ネットワーク (イントラネット) 内で発生する認証要求に対して、Windows Server 2012 R2 の Active Directory フェデレーションサービス (AD FS) (AD FS) で有効になっています。

AD FS 2016 には、Edge ブラウザーが WIA を実行できるようにする、改善された既定の設定が用意されています。また、Windows Phone を正しくキャッチすることもありません。

```
=~Windows\s*NT.*Edg.*
```

上記の方法では、頻繁に更新される場合でも、一般的なエッジシナリオをサポートするように個々のユーザーエージェント文字列を構成する必要がなくなりました。

他のブラウザーの場合は、AD FS プロパティ **Wiasupporteduseragents** を構成して、使用しているブラウザーに基づいて必要な値を追加します。  次の手順を使用できます。

### <a name="view-wiasupporteduseragent-settings"></a>WIASupportedUserAgent の設定を表示する

**Wiasupporteduseragents** は、WIA をサポートするユーザーエージェントを定義します。 AD FS は、ブラウザーまたはブラウザーコントロールでログインを実行するときに、ユーザーエージェント文字列を分析します。

現在の設定を表示するには、次の PowerShell の例を使用します。

```powershell
Get-AdfsProperties | select -ExpandProperty WiaSupportedUserAgents
```

![WIA サポート](../operations/media/Configure-AD-FS-Browser-WIA/wiasupport.png)

### <a name="change-wiasupporteduseragent-settings"></a>WIASupportedUserAgent の設定を変更する
既定では、新しい AD FS のインストールには、一連のユーザーエージェント文字列の一致が作成されます。 ただし、これらは、ブラウザーおよびデバイスの変更に基づいて古くなっている可能性があります。 特に、Windows デバイスでは、トークンに多少の違いがある同様のユーザーエージェント文字列があります。 次の Windows PowerShell の例では、シームレスな WIA をサポートする現在の市場にあるデバイスの現在のセットについて、最適なガイダンスを提供しています。

Windows Server 2012 R2 以前に AD FS がある場合は、次の手順を実行します。

```powershell
Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0","Windows NT 10.0; WOW64; Trident/7.0","MSIPC", "Windows Rights Management Client", "Edg/","Edge/")
```

Windows Server 2016 以降に AD FS がある場合は、次のようにします。

```powershell
Set-AdfsProperties -WIASupportedUserAgents @("MSIE 6.0", "MSIE 7.0; Windows NT", "MSIE 8.0", "MSIE 9.0", "MSIE 10.0; Windows NT 6", "Windows NT 6.3; Trident/7.0", "Windows NT 6.3; Win64; x64; Trident/7.0", "Windows NT 6.3; WOW64; Trident/7.0", "Windows NT 6.2; Trident/7.0", "Windows NT 6.2; Win64; x64; Trident/7.0", "Windows NT 6.2; WOW64; Trident/7.0", "Windows NT 6.1; Trident/7.0", "Windows NT 6.1; Win64; x64; Trident/7.0", "Windows NT 6.1; WOW64; Trident/7.0","Windows NT 10.0; WOW64; Trident/7.0", "MSIPC", "Windows Rights Management Client", "=~Windows\s*NT.*Edg.*")
```

上のコマンドは、AD FS が WIA の次のユースケースのみをカバーするようにします。

|ユーザーエージェント|ユース ケース|
|-----|-----|
|MSIE 6.0|IE 6.0|
|MSIE 7.0;Windows NT|IE 7、イントラネットゾーンの IE。 "Windows NT" フラグメントは、デスクトップオペレーティングシステムによって送信されます。|
|MSIE 8.0|IE 8.0 (デバイスがこれを送信することはないため、さらに具体的にする必要があります)|
|MSIE 9.0|IE 9.0 (デバイスがこれを送信することはないため、これをより具体的にする必要はありません)|
|MSIE 10.0;Windows NT 6|Windows XP およびそれ以降のバージョンのデスクトップオペレーティングシステムの IE 10.0</br></br>Windows Phone 8.0 デバイス (優先設定が mobile) は、送信されるため、除外されます。</br></br>ユーザーエージェント: Mozilla/5.0 (互換性あり)MSIE 10.0;Windows Phone 8.0;Trident/6.0;IEMobile/10.0;分岐強くNOKIALumia 920)|
|Windows NT 6.3;Trident/7.0</br></br>Windows NT 6.3;Win64x64Trident/7.0</br></br>Windows NT 6.3;WOW64Trident/7.0| Windows 8.1 デスクトップオペレーティングシステム、さまざまなプラットフォーム|
|Windows NT 6.2;Trident/7.0</br></br>Windows NT 6.2;Win64x64Trident/7.0</br></br>Windows NT 6.2;WOW64Trident/7.0|Windows 8 デスクトップオペレーティングシステム、さまざまなプラットフォーム|
|Windows NT 6.1;Trident/7.0</br></br>Windows NT 6.1;Win64x64Trident/7.0</br></br>Windows NT 6.1;WOW64Trident/7.0|Windows 7 デスクトップオペレーティングシステム、さまざまなプラットフォーム|
|Edg/および Edge/| Windows Server 2012 R2 以前の Microsoft Edge (Chromium) |
|=*~ Windows\s.**| Windows Server 2016 以降用 Microsoft Edge (Chromium)|
|MSIPC を右クリックし| Microsoft Information Protection and Control クライアント|
|Windows Rights Management クライアント|Windows Rights Management クライアント|

### <a name="additional-links"></a>その他のリンク

[Microsoft Edge のドキュメント](/microsoft-edge/web-platform/user-agent-string)
