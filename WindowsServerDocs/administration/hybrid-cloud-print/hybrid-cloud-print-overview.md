---
title: Windows Server ハイブリッドクラウド印刷の概要
description: ハイブリッドクラウド印刷を使用すると、IT 担当者は BYOD またはドメイン参加済みデバイスの印刷要件をサポートできます。
ms.topic: conceptual
author: trudyha
ms.author: trudyha
ms.date: 10/16/2017
ms.openlocfilehash: 0ba40c26b82bc5d5bd1a5b7f7b87d243fa8dff0e
ms.sourcegitcommit: 28b5ab74cb0b40539ccc1a83998d6391e87fe51f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96614824"
---
# <a name="windows-server-hybrid-cloud-print-overview"></a>Windows Server ハイブリッドクラウド印刷の概要

> 適用先:Windows Server 2016

## <a name="what-is-hybrid-cloud-print"></a>ハイブリッドクラウド印刷とは

**ハイブリッドクラウド印刷** は、 **オンデマンド機能** を通じて利用できる Windows Server 2016 の新機能です。 これにより、IT 担当者は自分のデバイスを持ち込むユーザーの印刷要件をサポートしたり、Azure Active Directory に参加しているデバイスを使用したりすることができます。 これには、windows phone、ラップトップ、または Windows 10 または Windows Mobile を実行しているタブレットなどのモバイルデバイスが含まれます。 どこからでもインターネットにアクセスできる印刷サポートが提供されます。

IT 管理者にとって、 **ハイブリッドクラウド印刷** では、Azure の multi-factor authentication を使用してユーザーアクセスを検証することで、オンプレミスのプリンターへのセキュリティで保護されたユーザーアクセスを提供します。 シングルサインオン (SSO) 機能により、ユーザーエクスペリエンスが簡略化されます。 **ハイブリッドクラウド印刷** は Windows **プリントサーバー** の役割に基づいて構築されており、IT プロフェッショナルはプリンターやユーザーアクセスのセキュリティを管理するのと同様のエクスペリエンスを提供しています。

**ハイブリッドクラウド印刷** を使用すると、組織内のユーザーが自分のデスクや職場から離れている場合でも、作業を完了するために使用するデバイスから印刷できます。

**ハイブリッドクラウド印刷** は、windows 10 の作成者 Update と Windows 10 S でサポートされています。

## <a name="feature-summary"></a>機能の概要

**ハイブリッドクラウド印刷** は、 **探索** サービスと **Windows プリント** サービスという2つの主要なサーバー側コンポーネントで構成されています。

- IIS サービスで実行されている **探索** サービスエンドポイントは、クラウドでのプリンター検出のための業界標準をサポートしています。

- 業界標準のインターネット印刷プロトコル (IPP) をサポートする IIS サービスで実行されている **Windows 印刷** サービスエンドポイント。これにより、広範なクライアント OS のサポートが実現します。

## <a name="deployment"></a>デプロイ

**ハイブリッドクラウド印刷** では、組織がユーザー認証を必要とする場所に応じて、いくつかの異なる展開オプションをサポートしています。 デプロイは次のようになります。

![ハイブリッドクラウド印刷ソリューションのグラフィックを示す図](../media/hybrid-cloud-print/wshcp-deployment-options.png)

*ハイブリッドクラウド印刷ソリューションの図*

図には次のように表示されます。

- ユーザー id プロバイダーとして Azure Active Directory を使用した **ハイブリッドクラウド印刷**。

- **Windows 印刷** サービスと **探索** サービスのエンドポイントが Azure Active Directory に登録され、クライアントデバイスは、これらのサービスに対して使用する必要なユーザー認証トークンを取得できるようになります。

- **Microsoft Intune** などの MDM サービスは、Azure Active Directory を **Windows プリント** サービスおよび **探索** サービスに接続するために必要なポリシーをクライアントデバイスにプロビジョニングします。

この表には、図の要素に関する詳細情報が含まれています。

| 要素 | 説明 |
|--|--|
| Azure Active Directory | ユーザーの id と承認の機能を提供し、制御します。 |
| Active Directory | ユーザーの id と承認の機能を提供し、制御します。 |
| Azure AD Connect | Azure AD とオンプレミスの AD との間でユーザーの資格情報を同期します。 |
| MDM サービス (Intune) | クライアントデバイス (BYOD デバイス) が企業のポリシーに準拠するように、デバイスポリシーのプロビジョニング機能を提供します。 |
| Azure AD プロキシ | は、ファイアウォールの内側から Azure に接続され、特定の構成されたアプリケーショントラフィックがインターネットから企業ネットワークに流れることができるようにする、有効期間の長い接続を提供します。 |
| Azure Web アプリ | ハイブリッドクラウド印刷ソリューションの中核となる部分。 は、プリンターを検出し、ドメインに参加していないデバイスの印刷コンテンツを送信するために必要な web エンドポイントを提供します。 |
| BYOD デバイス/Windows プリントサーバーのスプーラ/プリンタ | これらはそのようなものです。 デプロイの機能に変更はありません。 |

**ハイブリッドクラウド印刷** をインストールするには、次の2つの方法があります。

- * * 必要に応じて、役割と機能のファイルの追加と削除の詳細については、「 [Windows Server でのオンデマンド機能の構成](../server-manager/configure-features-on-demand-in-windows-server.md) 」を参照してください。

- * * Windows Server 2016 の設定、管理者は、[**設定**] [アプリ] [  ->  **Apps**  ->  **オプション機能の管理**] 機能を  ->  **追加** し、[オンデマンドで機能] パッケージを検索します。

- PowerShell コマンド-PowerShell 管理者ウィンドウで、次のコマンドを実行します。

```PowerShell
    Install-Module -Name PublishCloudPrinter
    Import-Module PublishCloudPrinter
```
