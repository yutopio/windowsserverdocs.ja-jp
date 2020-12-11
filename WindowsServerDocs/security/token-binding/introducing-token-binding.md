---
description: 詳細については、「トークンバインドの概要」を参照してください。
title: トークンバインドの概要
ms.topic: article
ms.assetid: 4623a48c-cefd-4a27-9173-2af58ac212f2
author: justinha
ms.author: Justinha
ms.date: 11/09/2016
ms.openlocfilehash: 8525ea1a052b4e2c4aaf8e40ed703172964092d3
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97044080"
---
# <a name="introducing-token-binding"></a>トークンバインドの概要

>適用対象: Windows Server 2016 および Windows 10

トークンバインドプロトコルを使用すると、アプリケーションとサービスは、セキュリティトークンを TLS レイヤーに暗号化して、トークンの盗難やリプレイ攻撃を軽減できます。
有効期間が長く、一意に識別できる TLS [RFC5246] のバインドは、複数の TLS セッションと接続にまたがることができます。

バージョンのサポート:

- Windows 10 バージョン 1507-既定でオフ
    - トークンバインドプロトコルが追加されました [[tokbind-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/01/)
    - WinInet & HTTP.SYS HTTP 経由のトークンバインドのサポート [[draft-tokbind-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/01/)
- Windows 10、バージョン1511および1607、および Windows Server 2016 –既定でオン
    - トークンバインドプロトコルが更新されました [[tokbind-01]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/01/)
    - トークンバインドネゴシエーションの TLS 拡張機能が追加されました [[tokbind-00]](https://tools.ietf.org/html/draft-popov-tokbind-negotiation-00)
    - WinInet & HTTP 更新によるトークンバインドのサポート HTTP.SYS [[draft-ietf-tokbind-02]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/02/)
- Windows 10、バージョン 1507 (サービス更新プログラム [KB4034668](https://support.microsoft.com/kb/KB4034668)、windows 10、バージョン1511、サービス更新 [KB4034660](https://support.microsoft.com/kb/KB4034660)、windows 10、バージョン1607、windows Server 2016 with サービス更新 [KB4034658](https://support.microsoft.com/kb/KB4034658) サポートトークンバインドプロトコルバージョン0.10 –既定)
    - トークンバインドプロトコルが更新されました [[tokbind-10]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/10/)
    - トークンバインドネゴシエーションの TLS 拡張機能が追加されました [[tokbind-05]](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)
    - WinInet & HTTP 更新によるトークンバインドのサポート HTTP.SYS [[draft-ietf-tokbind-06]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/06/)
- Windows 10 バージョン1703では、トークンバインディングプロトコルバージョン0.10 が既定でサポートされています。
    - トークンバインドプロトコルが更新されました [[tokbind-10]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-protocol/10/)
    - トークンバインドネゴシエーションの TLS 拡張機能が追加されました [[tokbind-05]](https://tools.ietf.org/html/draft-ietf-tokbind-negotiation-05)
    - WinInet & HTTP 更新によるトークンバインドのサポート HTTP.SYS [[draft-ietf-tokbind-06]](https://datatracker.ietf.org/doc/draft-ietf-tokbind-https/06/)
    - 仮想化ベースのセキュリティが有効になっている Windows デバイスは、実行中のオペレーティングシステムから分離された保護された環境でトークンバインドキーを保持します。

ASP .NET のサポートに関する情報については、 [.NET Framework リファレンスソースを参照](https://referencesource.microsoft.com/#System.Web/ITlsTokenBindingInfo.cs,4a5e5668f5c31170)してください。

.NET Framework の詳細については、次のトピックを参照してください。

- [ネットワークの機能強化](https://blogs.msdn.microsoft.com/dotnet/2015/11/30/net-framework-4-6-1-is-now-available/#networking)

- [.NET TokenBinding クラス](/dotnet/api/system.security.authentication.extendedprotection.tokenbinding?view=netframework-4.8)
