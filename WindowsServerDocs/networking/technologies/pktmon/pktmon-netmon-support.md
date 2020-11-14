---
title: Microsoft ネットワークモニター (Netmon) の Pktmon サポート
description: このページを使用して、パケットモニターによって生成された、Netmon 内の ETL ファイルを分析します。
ms.topic: how-to
author: khdownie
ms.author: v-kedow
ms.date: 11/12/2020
ms.openlocfilehash: 7c6e3a40558ea27a273464d157fa4fbdbacd7134
ms.sourcegitcommit: 8808f871c8cf131f819ef5540286218bd425da96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2020
ms.locfileid: "94632510"
---
# <a name="pktmon-support-for-microsoft-network-monitor-netmon"></a>Microsoft ネットワークモニター (Netmon) の Pktmon サポート

>適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows 10、Azure Stack HCI、Azure Stack Hub、Azure

パケットモニター (Pktmon) は、ETL 形式でログを生成します。 これらのログは、Microsoft ネットワークモニター (Netmon) を使用して特別なパーサーを使用して分析できます。 このトピックでは、パケットモニターによって生成された、Netmon 内の ETL ファイルを分析する方法について説明します。

## <a name="network-monitor-setup-and-configuration"></a>ネットワークモニターのセットアップと構成

次の手順に従って、パケットモニターで生成された ETL ファイルを解析するように Netmon をインストールし、構成します。

   1. [ネットワークモニター3.4 をインストール](/download/4865)します。
   1. 管理者特権でネットワークモニター開始し、Windows をアクティブパーサープロファイルとして設定します ([ツール]/[オプション]/[パーサープロファイル])。
   1. -Windows-PktMon-Events を [ここ](https://github.com/microsoft/NetMon_Parsers_for_PacketMon/blob/main/etl_Microsoft-Windows-PktMon-Events.npl)から   "%PROGRAMDATA%\Microsoft\Network monitor 3 \ Npl\ networkmonitor Parsers\Windows" に etl_Microsoft コピーします。
   1. -Windows-PktMon-Events を [ここ](https://github.com/microsoft/NetMon_Parsers_for_PacketMon/blob/main/stub_etl_Microsoft-Windows-PktMon-Events.npl) から "%PROGRAMDATA%\Microsoft\Network monitor 3 \ Npl\ networkmonitor Parsers\Windows\Stubs" に stub_etl_Microsoft コピーします。
   1. Stub_etl_Microsoft-Windows-PktMon-Events の名前を etl_Microsoft-Windows-PktMon-Events に変更します。
   1. NetworkMonitor_Parsers_sparser に etl_Microsoft-Windows-PktMon-Events を含めます。 npl in "%PROGRAMDATA%\Microsoft\Network Monitor 3 \ Npl\ networkmonitor パーサー"
   1. パーサーを再構築するには、管理者特権でネットワークモニターを再起動します。

