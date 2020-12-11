---
description: 詳細については、「従来の AD FS フェデレーションサーバープロキシを展開する」を参照してください。
ms.assetid: 1b21b0a9-1fe6-4fd1-8a25-92e578d774ed
title: AD FS でのフェデレーションサーバープロキシの展開
author: billmath
manager: femila
ms.date: 05/31/2017
ms.topic: article
ms.author: billmath
ms.openlocfilehash: 7798867f8445ee99835e883ccab771fa346b2673
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97044130"
---
# <a name="deploying-legacy-ad-fs-federation-server-proxies"></a>レガシ AD FS フェデレーションサーバープロキシの展開

Active Directory フェデレーションサービス (AD FS) AD FS でフェデレーションサーバープロキシを展開するには \( \) 、「 [チェックリスト: フェデレーションサーバープロキシの](Checklist--Setting-Up-a-Federation-Server-Proxy.md)セットアップ」の各タスクを実行します。

> [!NOTE]
> このチェックリストを使用する場合は、まず、サーバーの構成手順を開始する前に、 [Windows server 2012 の AD FS 設計ガイド](../design/ad-fs-design-guide-in-windows-server-2012.md) の「フェデレーションサーバープロキシの計画に関するガイダンス」を参照することをお勧めします。 このチェックリストに従うことで、フェデレーションサーバープロキシの設計と展開のプロセスについて理解を深めることができます。

## <a name="about-federation-server-proxies"></a>フェデレーションサーバープロキシについて
フェデレーションサーバープロキシは、Windows Server 2012 を実行するコンピューターであり、 &reg; プロキシの役割で動作するように手動で構成されている AD FS ソフトウェアです。 組織内のフェデレーション サーバー プロキシを使用して、インターネット クライアントと、企業ネットワーク上のファイアウォールの背後にあるフェデレーション サーバーの間で、仲介サービスを提供できます。

> [!NOTE]
> フェデレーションサーバーとフェデレーションサーバープロキシの役割を同じコンピューターにインストールすることはできませんが、フェデレーションサーバーはフェデレーションサーバープロキシ機能を実行できます。 詳細については、「 [When to Create a Federation Server](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dd807101(v=ws.11))」を参照してください。

Windows Server 2012 コンピューターに AD FS ソフトウェアをインストールし、 &reg; プロキシの役割で動作するように構成すると、そのコンピューターはフェデレーションサーバープロキシになります。

