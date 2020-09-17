---
title: ライブマイグレーショントラフィック用の少なくとも1つのネットワークで、少なくとも 1 Gbps のリンク速度が必要です
description: このベストプラクティスアナライザールールのテキストのオンラインバージョン。
ms.author: benarm
author: BenjaminArmstrong
ms.topic: article
ms.assetid: 5714df3f-f810-4618-8c93-e24881651100
ms.date: 8/16/2016
ms.openlocfilehash: cf1f09a635d6f6a46ee2a0bab2de53c898af9084
ms.sourcegitcommit: dd1fbb5d7e71ba8cd1b5bfaf38e3123bca115572
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2020
ms.locfileid: "90746297"
---
# <a name="at-least-one-network-for-live-migration-traffic-should-have-a-link-speed-of-at-least-1-gbps"></a>ライブマイグレーショントラフィック用の少なくとも1つのネットワークで、少なくとも 1 Gbps のリンク速度が必要です

>適用先:Windows Server 2016



|プロパティ|詳細|
|-|-|
|**オペレーティング システム**|Windows Server 2016|
|**製品/機能**|Hyper-V|
|**Severity**|エラー|
|**カテゴリ**|構成|

次のセクションでは、斜体は、この問題のためのベスト プラクティス アナライザー ツールで表示される UI テキストを示します。

## <a name="issue"></a>問題
*ライブマイグレーショントラフィックのネットワークには、少なくとも 1 Gbps のリンク速度がありません。*

## <a name="impact"></a>影響
*ライブマイグレーションが遅くなり、TCP 接続のタイムアウトによってネットワーク接続が中断される可能性があります。*

## <a name="resolution"></a>解決策
*1 Gbps 以上の速度でライブマイグレーションネットワークを少なくとも1つ構成してください。*

既存のネットワークアダプターが 1 Gbps 以上のリンク速度をサポートしているかどうかを確認するには、ネットワークハードウェアベンダーのドキュメントを参照してください。



