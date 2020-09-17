---
title: レプリケーションには証明書ベースの認証を使用することをお勧めします。
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: d931cc57-414f-4bdf-9ebd-08fd5e22b19d
ms.date: 8/16/2016
ms.openlocfilehash: 3ef11472c042e19de9f7ee52ea5958ca0bf6e44b
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90745857"
---
# <a name="certificate-based-authentication-is-recommended-for-replication"></a>レプリケーションには証明書ベースの認証を使用することをお勧めします。

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|警告|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*レプリケーション用に選択された1つ以上の仮想マシンが、Kerberos 認証用に構成されています。*

## <a name="impact"></a>**影響**
*プライマリサーバーからレプリケーションサーバーへのレプリケーションネットワークトラフィックは暗号化されていません。これは、次の仮想マシンに影響します。*

\<list of virtual machines>

## <a name="resolution"></a>**解決方法**
*暗号化を実行するために別の方法が使用されている場合は、無視してかまいません。それ以外の場合は、仮想マシンの設定を変更して、証明書ベースの認証を選択します。*



