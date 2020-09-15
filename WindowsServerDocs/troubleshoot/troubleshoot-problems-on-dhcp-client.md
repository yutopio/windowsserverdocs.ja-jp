---
title: DHCP クライアントでの問題のトラブルシューティング
description: この artilce では、DHCP クライアントの問題をトラブルシューティングし、データを収集する方法について説明します。
manager: dcscontentpm
ms.date: 5/26/2020
ms.topic: article
author: Deland-Han
ms.author: delhan
ms.openlocfilehash: d7cfe92272ad65ca4b413eb91039a9ab21de6c17
ms.sourcegitcommit: 7cacfc38982c6006bee4eb756bcda353c4d3dd75
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2020
ms.locfileid: "90078629"
---
# <a name="troubleshoot-problems-on-the-dhcp-client"></a>DHCP クライアントでの問題のトラブルシューティング

この記事では、DHCP クライアントで発生した問題をトラブルシューティングする方法について説明します。

## <a name="troubleshooting-checklist"></a>トラブルシューティングのチェックリスト

次のデバイスと設定を確認します。

  - ケーブルは接続され、動作しています。

  - MAC フィルタリングは、クライアントが接続されているスイッチで有効になっています。

  - ネットワークアダプターが有効になっています。

  - 正しいネットワークアダプタードライバーがインストールされ、更新されています。

  - DHCP クライアントサービスが開始され、実行されています。 これを確認するには、 **net start** コマンドを実行し、 **DHCP クライアント**を探します。

  - クライアントコンピューターで、ポート67と 68 UDP をブロックするファイアウォールはありません。

## <a name="event-logs"></a>イベント ログ

Microsoft-Windows-DHCP Client events/Operational および Microsoft-Windows-DHCP Client Events/Admin イベントログを確認します。 DHCP クライアントサービスに関連するすべてのイベントが、これらのイベントログに送信されます。
Microsoft-Windows-DHCP クライアントイベントは、[ **アプリケーションとサービスログ**] の [イベントビューアーにあります。

"Get NetAdapter-IncludeHidden" PowerShell コマンドは、ログに記録されているイベントを解釈するために必要な情報を提供します。 たとえば、インターフェイス ID や MAC アドレスなどです。

## <a name="data-collection"></a>データ コレクション

問題が発生したときに、DHCP クライアントとサーバー側の両方で同時にデータを収集することをお勧めします。 ただし、実際の問題によっては、DHCP クライアントまたは DHCP サーバー上で1つのデータセットを使用して調査を開始することもできます。

サーバーおよび影響を受けるクライアントからデータを収集するには、 [Wireshark](https://www.wireshark.org/download.html)を使用します。 DHCP クライアントと DHCP サーバーコンピューターで同時に収集を開始します。

問題が発生しているクライアントで、次のコマンドを実行します。

```console
ipconfig /release
ipconfig /renew
```

次に、クライアントとサーバーで Wireshark を停止します。 生成されたトレースを確認します。 少なくとも、通信が停止するステージを通知する必要があります。