---
title: リモート デスクトップ クライアント
description: すべてのデバイスで使うことができるさまざまなリモート デスクトップ クライアントについて説明します
ms.topic: article
ms.assetid: b7d8158c-aee1-4c60-8a46-40ce5595b8e8
author: HeidiLohr
manager: lizross
ms.author: helohr
ms.date: 10/22/2020
ms.localizationpriority: medium
ms.openlocfilehash: 70b9bfee5837af27576962698a408a45715bbd35
ms.sourcegitcommit: de9e13e0e74721d6edbecf4acc12465fff3d5df0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/24/2020
ms.locfileid: "92497055"
---
# <a name="remote-desktop-clients"></a>リモート デスクトップ クライアント

>適用先:Windows 10、Windows 8.1、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2

Microsoft リモート デスクトップ クライアントを使用することでリモート PC を制御できます。 クライアントは、モバイル スマートフォンなど、ほとんどすべてのデバイス上で実行できます。 クライアントでは、PC のキーボードにアクセスできる場合と同じようなことを行えます。 クライアントを使用すると、次のことができます。

- PC にインストールされているアプリを操作する。
- PC のファイルとネットワーク リソースにアクセスする。
- クライアントを終了するときに、アプリを開いたままにしておく。

開始する前に、[サポートされる構成](remote-desktop-supported-config.md)に関する記事を参照してください。 この記事では、リモート デスクトップ クライアントを接続できる PC 構成について説明します。 [クライアントに関する FAQ](remote-desktop-client-faq.md) の記事も参照してください。

次のクライアント アプリを利用できます。

| デバイス          | アプリの入手                                                                                                  | セットアップ手順                                                                |
|-----------------|-----------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
| Windows デスクトップ | [Windows デスクトップ クライアント](windowsdesktop.md#install-the-client)                                               | [Windows デスクトップ クライアントの概要](windowsdesktop.md) |
| Windows ストア   | [Microsoft Store の Windows 10 クライアント](https://go.microsoft.com/fwlink/?LinkID=616709)                   | [Microsoft Store クライアントの概要](windows.md)          |
| Android         | [Google Play の Android クライアント](https://play.google.com/store/apps/details?id=com.microsoft.rdc.android)     | [Android クライアントの概要](remote-desktop-android.md) |
| iOS             | [iTunes ストアの iOS クライアント](https://itunes.apple.com/app/microsoft-remote-desktop/id714464092?mt=8)     | [iOS クライアントの概要](remote-desktop-ios.md)         |
| macOS           | [iTunes ストアの macOS クライアント](https://itunes.apple.com/app/microsoft-remote-desktop/id1295203466?mt=12) | [macOS クライアントの概要](remote-desktop-mac.md)       |

## <a name="configuring-the-remote-pc"></a>リモート PC の構成

リモートでアクセスする前にリモート PC を構成するには、「[PC へのアクセスを許可する](remote-desktop-allow-access.md)」を参照してください。

## <a name="remote-desktop-client-uri-scheme"></a>リモート デスクトップ クライアントの URI スキーム

統一リソース識別子 (URI) スキームを有効にすると、プラットフォーム間でリモート デスクトップ クライアントの機能を統合できます。 iOS、Mac、Android クライアントで使うことができる[サポートされている URI 属性](remote-desktop-uri.md)を確認してください。
