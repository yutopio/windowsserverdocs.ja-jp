---
title: Windows Server バージョン 2004 と 20H2 の新機能
description: Windows Server バージョン 2004 と 20H2 の新機能。
ms.topic: article
author: Heidilohr
ms.author: helohr
ms.date: 05/27/2020
ms.localizationpriority: high
ms.openlocfilehash: f44dcc7a1c7fab2d99f0358794bd5b2aedb87b75
ms.sourcegitcommit: b82dfbfdc5df1327feb8be053a760739b01e3031
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/20/2020
ms.locfileid: "92255869"
---
# <a name="whats-new-in-windows-server-version-2004-and-20h2"></a>Windows Server バージョン 2004 および 20H2 の新機能

>適用先:Windows Server (半期チャネル)

Windows の最新の機能については、「[Windows Server の新機能](whats-new-in-windows-server.md)」を参照してください。 このトピックでは、Windows Server バージョン 2004 と 20H2 の新機能の一部について説明します。

Windows Server バージョン 20H2 は、Windows Server バージョン 2004 の半期チャネルの次回のリリースです。 このバージョンでは、信頼性、パフォーマンス、およびその他の一般的な機能強化に焦点を当てていますが、新機能はありません。 他の半期チャネル リリースと同様に、リリースから 18 か月間サポートされます。 半期チャネル リリースのサポート日付の詳細については、「[Windows Server のリリース情報](windows-server-release-info.md)」を参照してください。

## <a name="server-core-container-improvements"></a>Server Core コンテナーの機能強化

ダウンロードの速度とパフォーマンスを向上させるために、Server Core コンテナー イメージの全体的なサイズを縮小しました。 次の点が強化されています。

- イメージ サイズが小さくなるように、Server Core コンテナー イメージからほとんどの NGEN イメージを削除しました。
- Server Core コンテナーイメージ上に構築された .NET Framework のランタイム イメージが、ASP.NET アプリと Windows PowerShell スクリプトのパフォーマンス用に最適化されました。
- また、.NET チームでは、各 NGEN イメージのコピーが 1 つだけになるようにし、.NET Framework イメージのサイズが小さくなりました。

これらのコンテナーのサイズをよりよく理解できるように、次の表では、[2020 年 5 月のマンスリー セキュリティ更新プログラム](https://support.microsoft.com/help/4561769/windows-server-containers-for-may-2020) ("5B" 更新プログラムとも呼ばれます) 時点での現在のバージョンを以前のバージョンと比較しています。

| コンテナー バージョン | ダウンロード サイズ | ディスク上のサイズ |
|---|---|---|
| Windows Server バージョン 1903 | 2.311 GB | 5.1 GB |
| Windows Server バージョン 1909 | 2.257 GB | 4.97 GB |
| Windows Server バージョン 2004 | 1.830 GB | 3.98 GB |

Windows Server バージョン 2004 更新プログラムの詳細については、[ブログ投稿](https://techcommunity.microsoft.com/t5/containers/windows-server-version-2004-now-available/ba-p/1419194)を参照してください。 Windows コンテナーの全般的な更新プログラムの詳細については、「[Windows Server のコンテナーの更新](/virtualization/windowscontainers/deploy-containers/update-containers/)」を参照してください。
