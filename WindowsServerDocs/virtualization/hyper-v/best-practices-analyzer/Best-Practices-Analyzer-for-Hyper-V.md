---
title: Hyper-v のベストプラクティスアナライザー
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 3747faa5-6e9f-499e-8a79-3fb9d73b6b92
ms.date: 8/16/2016
ms.openlocfilehash: c48f94eef1ceb77e80701adca9aeddfb4656e53c
ms.sourcegitcommit: 6931830a70c5849d8f884cdc7bd4f5afc1a00cce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2020
ms.locfileid: "91955817"
---
# <a name="best-practices-analyzer-for-hyper-v"></a>Hyper-v のベストプラクティスアナライザー

> 適用先:Windows Server 2016

Windows の管理の*ベスト プラクティス*とは、標準的な環境の下で、専門家の定義に従ってサーバーを構成するための望ましい方法と考えられるガイドラインです。 ベストプラクティス違反は、重要なものであっても、必ずしも問題を引き起こすとは限りません。 ただし、パフォーマンスの低下、信頼性の低下、予期しない競合、セキュリティリスクの増大、またはその他の潜在的な問題の原因となる可能性のあるサーバー構成を示すことができます。

ベストプラクティスアナライザーは、これらのベストプラクティスに基づくルールを使用してコンピューターをスキャンし、結果を報告します。 各ベストプラクティス規則には、規則に準拠する方法の詳細が含まれています。 このセクションでは、Hyper-v に適用されるベストプラクティスを理解するのに役立つこれらの規則について説明します。また、ベストプラクティスに準拠していない条件がスキャンによって検出された場合の結果も解釈します。

ベストプラクティスアナライザーとスキャンの詳細については、「 [ベストプラクティスアナライザー](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-r2-and-2012/dn283329(v=ws.11))」を参照してください。

## <a name="about-hyper-v"></a>Hyper-V について
Hyper-v を使用すると、1台の物理コンピューターで複数のオペレーティングシステムを同時に実行することができます。 Virtual machines を使用すると、コンピューティングリソースをより効率的かつ柔軟に使用できます。 Hyper-v の詳細については、「 [Windows Server 2016 の hyper-v](../Hyper-V-on-Windows-Server.md)」を参照してください。



