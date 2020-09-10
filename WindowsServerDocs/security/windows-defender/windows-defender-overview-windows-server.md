---
title: Windows Server 用 windows Defender の概要
description: Windows Server のセキュリティ
ms.topic: article
ms.assetid: 751efb33-a08e-4e90-9208-6f2bc319e029
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/12/2016
ms.openlocfilehash: 4ed6a8f9fc9618156963bd2b3c51e4819d8adb36
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89638645"
---
# <a name="windows-defender-antivirus-for-windows-server"></a>Windows Server 用 windows Defender ウイルス対策

>適用先:Windows Server 2016

Windows Server 2016 に Windows Defender ウイルス対策が含まれるようになりました。 Windows Defender AV は、Windows Server 2016 を既知のマルウェアに対して直ちかつ積極的に保護し、Windows Update によってマルウェア対策の定義を定期的に更新することができるマルウェア対策です。

詳細については、Windows 10 ドキュメントライブラリの [Windows Defender ウイルス対策](/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-in-windows-10) に関するドキュメントを参照してください。


Windows 10 でも Windows Server 2016 でも Windows Defender AV の機能、構成、管理の大部分は同じですが、次のような主な違いがあります。

- Windows Server 2016 では、定義したサーバーの役割に基づいて[自動除外](/windows/threat-protection/windows-defender-antivirus/configure-server-exclusions-windows-defender-antivirus)が適用されます。
- Windows Server 2016 では、他のウイルス対策製品を実行していても Windows Defender AV は無効になりません。

Windows [server 2016 の Windows Defender ウイルス対策](/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016) に関するトピックには、次の方法を含む、windows server 2016 に固有のセットアップおよび構成情報が含まれています。

-   [インターフェイスを有効にする](/windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_UsingDef)

-   [Windows Defender AV が実行中であることを確認する]( /windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefRun)

-   [マルウェア定義の更新]( /windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_UpdateDef)

-   [サンプルの送信]( /windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefSamples)

-   [自動除外を構成する]( /windows/threat-protection/windows-defender-antivirus/windows-defender-antivirus-on-windows-server-2016#BKMK_DefExclusions)