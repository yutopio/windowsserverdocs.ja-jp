---
title: Windows Server 2008 Foundation から Windows Server Essentials への移行
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: f22fc0a4-cb82-4e60-afe6-2d03145745e7
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 7ccb0e79094c5d3393b9548fc733224fd8fa9cbf
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89625874"
---
# <a name="migrate-windows-server-2008-foundation-to-windows-server-essentials"></a>Windows Server 2008 Foundation から Windows Server Essentials への移行

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

このガイドでは、既存の Windows Server 2008 Foundation ドメインを &reg; 新しいハードウェア上の Windows server 2012 Essentials に移行してから、設定とデータを移行する方法について説明します。 このガイドでは、移行の完了後に Windows Server Essentials ネットワークから既存のサーバーを削除する方法についても説明します。

> [!NOTE]
>  移行中の問題を回避するために、Windows Server Essentials 製品開発チームでは、移行を開始する前にこのドキュメントを読むことを強くお勧めします。

## <a name="additional-resources"></a>その他のリソース
 追加情報、ツール、および移行プロセスの実行を支援するコミュニティ リソースへのリンクについては、[Windows Small Business Server への移行 ](https://go.microsoft.com/fwlink/?LinkId=217520) を参照してください。

## <a name="terms-and-definitions"></a>用語と定義
 **移行元サーバー:** 設定とデータの移行元の既存のサーバー。

 **移行先サーバー:** 設定とデータの移行先となる新しいサーバー。

## <a name="migration-process-summary"></a>移行プロセスの概要
 この移行ガイドには次の手順が含まれます。


1.  [Windows Server Essentials への移行のために移行元サーバーを準備](Prepare-your-Source-Server-for-Windows-Server-Essentials-migration.md)します。  移行元サーバーおよびネットワークが、移行できる状態になっていることを確認する必要があります。 ここでは、移行元サーバーのバックアップ、移行元サーバーのシステム正常性の評価、最新のサービス パックと修正プログラムのインストール、およびネットワーク構成の確認について詳しく説明します。

2.  [Windows Server Essentials を移行モードでインストール](Install-Windows-Server-Essentials-in-migration-mode.md)します。  ここでは、移行先サーバーに Windows Server Essentials を移行モードでインストールするために実行する手順について説明します。

3.  [新しい Windows Server Essentials ネットワークにコンピューターを参加](Join-computers-to-the-new-Windows-Server-Essentials-network.md)させます。  このセクションでは、クライアントコンピューターを新しい Windows Server Essentials ネットワークに参加させ、グループポリシーの設定を更新する方法について説明します。

4.  [Windows Server 2008 Foundation の設定とデータを移行先サーバーに移動](./move-windows-server-2008-foundation-to-the-destination-server-for-migration.md)します。  ここでは、移行元サーバーからのデータと設定の移行について説明します。

5.  [新しい Windows Server Essentials ネットワークから移行元サーバーを降格し、削除](Demote-and-remove-the-Source-Server-from-the-new-Windows-Server-Essentials-network.md)します。  移行元サーバーをネットワークから削除する前に、グループ ポリシーの更新を強制し、移行元サーバーを降格する必要があります。

6.  [Windows Server Essentials への移行のために移行後のタスクを実行](Perform-post-migration-tasks-for-Windows-Server-Essentials-migration.md)します。  すべての設定とデータを Windows Server Essentials に移行したら、許可されたコンピューターをユーザーアカウントにマップすることができます。

7.  [Windows Server Essentials ベストプラクティスアナライザーを実行](Run-the-Windows-Server-Essentials-Best-Practices-Analyzer.md)します。  Windows Server Essentials への設定とデータの移行が完了したら、Windows Server Essentials BPA を実行する必要があります。


 いくつかの移行手順では、管理者としてコマンド プロンプト ウィンドウを開く必要があります。

###  <a name="to-open-a-command-prompt-window-on-the-source-server-as-an-administrator"></a><a name="BKMK_OpenACommandPromptAsAdmin"></a> 移行元サーバーで管理者としてコマンドプロンプトウィンドウを開くには

1.  **[開始]** をクリックします。

2.  検索ボックスに「**cmd**」と入力します。

3.  結果一覧で **[cmd]** を右クリックし、**[管理者として実行]** をクリックします。

#### <a name="to-open-a-command-prompt-window-on-the-destination-server-as-an-administrator"></a>移行先サーバーで管理者としてコマンド プロンプト ウィンドウを開くには

1.  [**スタート**] 画面で、検索ボックスに「**cmd**」と入力します。

2.  結果一覧で **[cmd]** を右クリックし、**[管理者として実行]** をクリックします。