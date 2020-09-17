---
title: Active Directory ドメインコントローラーとして構成されているコンピューターに RemoteFX をインストールしないようにする
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: da58694e-91f6-45d8-a599-18966db165f4
ms.date: 8/16/2016
ms.openlocfilehash: 1f639998c568035d0c992403cd0b1056ea4607b5
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90747057"
---
# <a name="avoid-installing-remotefx-on-a-computer-that-is-configured-as-an-active-directory-domain-controller"></a>Active Directory ドメインコントローラーとして構成されているコンピューターに RemoteFX をインストールしないようにする

>適用先:Windows Server 2016

ベスト プラクティスおよびスキャンの詳細については、「[ベスト プラクティス アナライザー スキャンの実行とスキャン結果の管理](https://go.microsoft.com/fwlink/p/?LinkID=223177)」を参照してください。

|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|エラー|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>**問題点**
*RemoteFX はドメインコントローラーにインストールされます。*

## <a name="impact"></a>**影響**
*RemoteFX 用に構成された仮想コンピューターは、これらのコンピューターでは使用できません。*

## <a name="resolution"></a>**解決方法**
*このサーバーを Hyper-v 用 RemoteFX または Active Directory ドメインコントローラーとして構成するかどうかを決定し、必要に応じてサーバーを再構成します。*



