---
description: '詳細情報: サイトリンクプロパティの設定'
ms.assetid: de054ac2-a386-43ec-a537-c0de21549741
title: サイト リンクのプロパティを設定する
author: iainfoulds
ms.author: daveba
manager: daveba
ms.date: 05/31/2017
ms.topic: article
ms.openlocfilehash: 135af3ae1d910ec0a8315eeb168fd03d2e4e1a71
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97049320"
---
# <a name="setting-site-link-properties"></a>サイト リンクのプロパティを設定する

>適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

サイト間レプリケーションは、接続オブジェクトのプロパティに従って実行されます。 知識整合性チェッカー (KCC) は、接続オブジェクトを作成するときに、サイトリンクオブジェクトのプロパティからレプリケーションスケジュールを取得します。 各サイトリンクオブジェクトは、2つ以上のサイト間のワイドエリアネットワーク (WAN) 接続を表します。

サイトリンクオブジェクトのプロパティの設定には、次の手順が含まれます。

-   そのレプリケーションパスに関連付けられているコストを確認します。 KCC はコストを使用して、同じディレクトリパーティションをレプリケートする2つのサイト間のレプリケーションに最もコストのかからないルートを決定します。

-   サイト間レプリケーションが実行される時間を定義するスケジュールを決定する。

-   レプリケーションが許可されている時間帯にレプリケーションを実行する頻度を定義するレプリケーション間隔を決定します。スケジュールに従って定義します。

## <a name="in-this-guide"></a>このガイドの内容

-   [コストを決定する](../../ad-ds/plan/Determining-the-Cost.md)

-   [スケジュールを決定する](../../ad-ds/plan/Determining-the-Schedule.md)

-   [間隔を決定する](../../ad-ds/plan/Determining-the-Interval.md)



