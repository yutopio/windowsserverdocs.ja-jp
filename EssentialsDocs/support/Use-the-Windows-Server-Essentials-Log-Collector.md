---
title: Windows Server Essentials Log Collector の使用
description: Windows Server Essentials の使用方法について説明します。
ms.date: 10/03/2016
ms.topic: article
ms.assetid: c6985518-b42d-4cfb-9761-eaa75306b6d7
author: nnamuhcs
ms.author: geschuma
manager: mtillman
ms.openlocfilehash: 07e849fa8db3cdc4204de402c6fc0cb823881480
ms.sourcegitcommit: db2d46842c68813d043738d6523f13d8454fc972
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2020
ms.locfileid: "89624994"
---
# <a name="use-the-windows-server-essentials-log-collector"></a>Windows Server Essentials Log Collector の使用

>適用対象: windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials

コンピューターの問題のトラブルシューティングを行うときに、Microsoft カスタマーサービスサポートの担当者から、Windows Server Essentials Log Collector を使用して、サーバー、ネットワーク上のコンピューター、またはその両方からログを収集するように指示される場合があります。

 Log Collector は、プログラム ログ、イベント レビュー担当者のログ、および関連する環境情報を指定された場所で 1 つの ZIP ファイルにコピーします。 サーバーまたはネットワーク上のコンピューターから、またはコンピューターへのリモート接続を使用して、Log Collector を実行できます。

> [!NOTE]
>Log Collector がネットワークの問題を分析したり、サーバーやネットワーク上のコンピューターに変更を加えることはありません。 ネットワークの問題をトラブルシューティングする方法の詳細については、サーバー製品のヘルプ ドキュメントを参照してください。
>このガイドでは、サーバー以外のネットワーク上のコンピューターをネットワークコンピューターと呼びます。
>
>[Windows Server Essentials Log Collector インストールパッケージをダウンロード](https://www.microsoft.com/download/details.aspx?id=34821)します。

 Log Collector をインストールし実行するには、次のトピックの手順を実行します。

1. [Log Collector のインストール](../support/Install-the-Windows-Server-Essentials-Log-Collector.md)

2. [Log Collector の実行](../support/Run-the-Windows-Server-Essentials-Log-Collector.md)


## <a name="environment-information-collected"></a>収集される環境情報
 指定したネットワーク コンピューターまたはサーバーごとに、Log Collector は次の環境情報を収集し、ログ コレクション ファイルに配置します。

-   オペレーティング システムのバージョン

-   CPU の製造元と説明

-   メモリ量と割り当て

-   TCP/IP にバインドされているネットワーク アダプター

-   Locale

-   処理

-   ストレージの構成

-   ホスト ファイルの情報

-   アプリケーション、システム、Windows Server、Media Center などのイベント ログ

-   サービス コントロール マネージャー メッセージ

-   再起動イベントと Windows Update イベント

-   システム エラーとアプリケーション エラー

## <a name="services-information-collected"></a>収集されるサービス情報

### <a name="server-services"></a>サーバーのサービス

-   Windows Server クライアント コンピューターのバックアップ サービス

-   Windows Server クライアント コンピューターのバックアップ プロバイダー サービス

-   Windows Server デバイス プロバイダー

-   Windows Server ドメイン名管理

-   Windows Server サービス プロバイダー レジストリ

-   Windows Server の設定プロバイダー

-   Windows Server UPnP デバイス サービス

-   Windows Server リモート Web アクセスの管理プロバイダー

-   Windows Server の正常性サービス

-   Windows Server の記憶域サービス

-   Windows Server SQM サービス

### <a name="network-computer-services"></a>ネットワーク コンピューターのサービス

-   Windows Server クライアント コンピューターのバックアップ プロバイダー サービス

-   Windows Server の正常性サービス

-   Windows Server サービス プロバイダー レジストリ

-   Windows Server SQM サービス

## <a name="logs-and-registry-information-collected"></a>収集されるログとレジストリ情報
 Log Collector は、指定されたネットワーク コンピューターまたはサーバーごとに、サーバーとネットワーク コンピューターから次のようにログとレジストリ情報を収集します。

### <a name="server-logs-and-registry-information"></a>サーバー ログとレジストリ情報

-   <ProgramData \Microsoft\Windows サーバーログのサーバー製品ログ \>

-   スケジュールされたタスク

-   API のセットアップ ログ

-   Windows Update のログ

-   正常性アラート ファイル

-   デバイス情報ファイル

-   サーバー バックアップのログ ファイル

-   Panther ログ ファイル

-   サービス

-   次に配置されたレジストリ キー

    -   \\\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows サーバー \

    -   \\\ HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\DevicesProviderSvc

    -   \\\ HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\DomainManagerProviderSvc

### <a name="network-computer-logs-and-registry-information"></a>ネットワーク コンピューターのログおよびレジストリ情報

-   <ProgramData \Microsoft\Windows のネットワークコンピューターの製品ログ \>

-   <ProgramData \Microsoft\Windows のデータファイルにある正常性アラートファイル \>

-   Windows Update のログ

-   API のセットアップ ログ

-   スケジュールされたタスクの情報

-   \\HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows サーバー \ からのレジストリキー

## <a name="logs-for-computers-that-do-not-run-a-version-of-the-windows-operating-system"></a>Windows 版のオペレーティング システムを実行していないコンピューターのログ
 Log Collector は Windows 版のオペレーティング システムを実行していないコンピューターからログ ファイルを収集しません。 Windows 以外のコンピューターの場合、次のログ ファイルを Log Collector ファイルを保存しているのと同じ場所に手動でコピーします。

-   System.log

-   Library/Logs/Windows Server.log

-   Library/Logs/CrashReporter/スタートパッド-<nnn \> (スタートパッドのすべての <nnn \> . crash ファイルをコピーする)

-   Library/Logs/DiagnosticReports/スタートパッド-<nnn \> (スタートパッドのすべての <nnn \> . crash ファイルをコピーする)

## <a name="see-also"></a>こちらもご覧ください

-   [Log Collector エラーのトラブルシューティング](../support/Troubleshoot-Windows-Server-Essentials-Log-Collector-Errors.md)

