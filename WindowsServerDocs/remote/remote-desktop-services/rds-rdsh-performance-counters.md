---
title: パフォーマンス カウンターを使用して、リモート デスクトップ セッション ホストでアプリケーションの応答性の問題を診断するには
description: アプリの動作が遅い RDS のでしょうか。 RDSH のアプリのパフォーマンスに関する問題を診断に使用できるパフォーマンス カウンターについて説明します
ms.prod: windows-server-threshold
ms.technology: remote-desktop-services
ms.author: elizapo
ms.date: 09/19/2018
ms.tgt_pltfrm: na
ms.topic: article
author: lizap
manager: dougkim
ms.localizationpriority: medium
ms.openlocfilehash: 241b2b776a68cf5aec68a4d331201a07f0e5ea53
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59844653"
---
# <a name="use-performance-counters-to-diagnose-app-performance-problems-on-remote-desktop-session-hosts"></a>パフォーマンス カウンターを使用して、リモート デスクトップ セッション ホストでのアプリ パフォーマンスの問題を診断するには

アプリケーション パフォーマンスの低下を診断する最も困難な問題の 1 つは、アプリケーションの実行速度が遅いか応答しません。 これまでは、収集の CPU、メモリ、ディスク入力/出力、およびその他のメトリックによって、診断を開始し、問題の原因を解明しようとする Windows パフォーマンス アナライザーなどのツールを使用します。 残念ながらほとんどの状況でこのデータ問題が解決しないリソースの消費量のカウンターが頻繁かつ大規模なバリエーションがあるため、根本原因を特定します。 データを読み取り、報告された問題に関連付けが困難になります。 役立つアプリ パフォーマンスの問題を迅速に解決の詳細は、いくつかの新しいパフォーマンス カウンターが追加されました (使用可能な[をダウンロードする](#download-windows-server-insider-software)を通じて、 [Windows Insider Program](https://insider.windows.com)) そのメジャーのユーザーがフローを入力します。

ユーザー入力の遅延のカウンターは、不適切なエンド ユーザーが RDP エクスペリエンスの根本原因をすばやく特定するのに役立ちます。 このカウンターはどのくらいの時間、ユーザーの (マウスやキーボードの使用状況) などの入力キューに残ります、プロセスによって取得される前に測定し、カウンターは、ローカルとリモートの両方のセッションで動作します。

次の図は、クライアントからアプリケーションにユーザー入力のフローの大まかな表現を示します。

![リモート デスクトップ-アプリケーションにユーザーのリモート デスクトップ クライアントからのユーザー入力フロー](.\media\rds-user-input.png)

ユーザーの入力遅延カウンタ (内の時間間隔) 入力キューに登録されるアプリで取得される場合と最大デルタを測定する、[従来のメッセージ ループ](https://msdn.microsoft.com/library/windows/desktop/ms644927.aspx#loop)次のフロー チャートのように。

![リモート デスクトップ - ユーザー入力の遅延のパフォーマンス カウンターのフロー](.\media\rds-user-input-delay.png)

このカウンターの 1 つの重要な詳細は、構成可能な時間内で最大のユーザーの入力遅延を報告します。 これは、入力に、アプリケーションは、入力などの重要なと表示の操作の速度に影響する可能性に到達するためにかかる最長時間。

たとえば、次の表にユーザー入力の遅延として報告されます 1,000 ms この間隔内で。 報告が「低」のユーザーの認識は、入力の中で最も遅い時刻によって決定されるため、最も低速なユーザーが、間隔の遅延を入力 (最大)、すべての合計入力の平均速度ではなくが発生しました。

|数値| 0 | 1 | 2 |
|------|---|---|---|
|遅延 |16 ミリ秒| 20 ミリ秒| 1,000 ms|

## <a name="enable-and-use-the-new-performance-counters"></a>有効にして、新しいパフォーマンス カウンターの使用

これらの新しいパフォーマンス カウンターを使用するには、このコマンドを実行してレジストリ キーをまず有効にする必要があります。

```
reg add "HKLM\System\CurrentControlSet\Control\Terminal Server" /v "EnableLagCounter" /t REG_DWORD /d 0x1 /f
```

>[!NOTE]
> Windows 10 では 1809 またはそれ以降のバージョンまたは Windows Server 2019 以降を使用している場合は、レジストリ キーを有効にする必要はありません。

次に、サーバーを再起動します。 パフォーマンス モニターを開きし、次のスクリーン ショットに示すように、プラス記号 (+) を選択します。

![リモート デスクトップのユーザーを追加する方法を示すスクリーン ショットは、遅延のパフォーマンス カウンターを入力](.\media\rds-add-user-input-counter-screen.png)

その後、必要がありますカウンターの追加ダイアログ ボックスが表示、選択できる**プロセスごとのユーザーの入力遅延**または**セッションごとのユーザーの入力遅延**します。

![リモート デスクトップのセッションごとのユーザーの入力遅延を追加する方法を示すスクリーン ショット](.\media\rds-user-delay-per-session.png)

![リモート デスクトップのプロセスごとのユーザーの入力遅延を追加する方法を示すスクリーン ショット](.\media\rds-user-delay-per-process.png)

選択した場合**プロセスごとのユーザーの入力遅延**が表示されます、 **、選択したオブジェクトのインスタンス**(つまり、プロセス) で```SessionID:ProcessID <Process Image>```形式。

電卓アプリケーションが実行されている場合など、[セッション ID 1](https://msdn.microsoft.com/library/ms524326.aspx)、わかります```1:4232 <Calculator.exe>```します。

> [!NOTE]
> すべてのプロセスが含まれます。 システムとして実行されている任意のプロセスは表示されません。

カウンターは、ユーザー入力の遅延を追加するとすぐにレポートを開始します。 既定では、最大の小数点以下桁数が 100 (ミリ秒) に設定に注意してください。 

![リモート デスクトップのユーザーの入力遅延パフォーマンス モニターでプロセスごとのアクティビティの例](.\media\rds-sample-user-input-delay-perfmon.png)

次に、見て、**セッションごとのユーザーの入力遅延**します。 各セッション ID のインスタンスがあるし、カウンターは、指定したセッション内で任意のプロセスのユーザーの入力遅延を表示します。 さらに、"Max"(、最大ユーザー入力の遅延のすべてのセッション間で)"と"Average"(平均 acorss すべてのセッション)"という 2 つのインスタンスがあります。

次の表では、これらのインスタンスの表示例を示します。 (できます情報を取得する、同じパフォーマンス モニターでレポートのグラフの種類に切り替えることによって。)

|カウンターの種類|［インスタンス名］|報告される遅延 (ミリ秒)|
|---------------|-------------|-------------------|
|プロセスごとのユーザー入力の遅延|1:4232 <Calculator.exe>|  200|
|プロセスごとのユーザー入力の遅延|2:1000 <Calculator.exe>|  16|
|プロセスごとのユーザー入力の遅延|1:2000 <Calculator.exe>|  32|
|セッションごとのユーザー入力の遅延|1|    200|
|セッションごとのユーザー入力の遅延|2|    16|
|セッションごとのユーザー入力の遅延|平均|  108|
|セッションごとのユーザー入力の遅延|最大|  200|

## <a name="counters-used-in-an-overloaded-system"></a>オーバー ロードされたシステムで使用されるカウンター

これで何が表示レポートでアプリのパフォーマンスが低下した場合を見てみましょう。 次のグラフは、Microsoft Word でリモートで作業しているユーザーの測定値を示しています。 この場合は、RDSH サーバーのパフォーマンスがより多くのユーザーのログインと時間の経過と共に低下します。

![リモート デスクトップの Microsoft Word を実行している RDSH サーバーのパフォーマンス グラフの例](.\media\rds-user-input-perf-graph.png)

グラフの行を読み取る方法を次に示します。

- ピンクの線は、サインインしているサーバー上のセッションの数を示します。
- 赤い線は、CPU 使用率です。
- 緑の線は、すべてのセッション間で最大のユーザーの入力遅延です。
- (このグラフで色が黒として表示されます)、青い線は、すべてのセッションで平均的なユーザー入力の遅延を表します。

CPU のスパイクとユーザー入力の遅延の間の相関関係があることがわかります: ユーザー入力の遅延が増加で、CPU は、複数の使用状況を取得します。 またより多くのユーザーを取得、システムに追加されるため、CPU 使用率をより頻繁にユーザー入力の遅延の急増に先頭の 100% に近い取得します。 このカウンターはリソース不足になるサーバーを実行する場合に非常に便利ですは、特定のアプリケーションに関連するのにユーザー入力の遅延を追跡するためにも使用できます。

## <a name="configuration-options"></a>構成オプション

既定では 1,000 ミリ秒、間隔でユーザー入力の遅延をレポートには、このパフォーマンス カウンターを使用する際に重要なことです。 パフォーマンス カウンターのサンプル間隔のプロパティ (ように設定する次のスクリーン ショットで) 別に、報告された値は正しいされません。

![リモート デスクトップのパフォーマンス モニターのプロパティ](.\media\rds-user-input-perfmon-properties.png)

これを解決するには、使用する間隔 (ミリ秒単位) を一致するように、次のレジストリ キーを設定できます。 たとえばを 5 秒にサンプル x 秒ごとを変更した場合このキーを 5000 ミリ秒に設定する必要があります。

```
[HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Terminal Server]

"LagCounterInterval"=dword:00005000
```

>[!NOTE]
>Windows 10 では 1809 またはそれ以降のバージョンまたは Windows Server 2019 以降を使用している場合は、パフォーマンス カウンターを解決する LagCounterInterval を設定する必要はありません。

また、同じレジストリ キーの下に役に立つキーをいくつかが追加されました。

**LagCounterImageNameFirst** -キーを押す`DWORD 1`(既定値 0 またはキーが存在しない)。 カウンター名「イメージ名 < SessionID:ProcessId >」に変更します。 たとえば、「< 1:7964 > エクスプ ローラー」 これは、イメージ名で並べ替えを行う場合に便利です。

**LagCounterShowUnknown** -キーを押す`DWORD 1`(既定値 0 またはキーが存在しない)。 これには、サービスまたはシステムとして実行されているすべてのプロセスが表示されます。 一部のプロセスとして設定のセッションで表示されます"?."

これは、何両方のキーが有効にするように見えます。

![リモート デスクトップ-で両方のキーを持つパフォーマンス モニター](.\media\rds-user-input-delay-with-two-counters.png)

## <a name="using-the-new-counters-with-non-microsoft-tools"></a>Microsoft 以外のツールを使用して、新しいカウンターを使用してください。

使用してこのカウンターを使用できる監視ツール、 [Perfmon API](https://msdn.microsoft.com/library/windows/desktop/aa371903.aspx)します。

## <a name="download-windows-server-insider-software"></a>Windows Server Insider ソフトウェアをダウンロードします。

登録されている内部関係者に直接移動できる、 [Windows Server Insider プレビューのダウンロード ページ](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver)Insider の最新版のソフトウェアをダウンロードします。  内部関係者として登録する方法については、次を参照してください。 [Server 入門](https://insider.windows.com/en-us/for-business-getting-started-server/)します。

## <a name="share-your-feedback"></a>フィードバックを共有します。

フィードバック Hub を使用してこの機能のフィードバックを送信することができます。 選択**アプリ > 他のすべてのアプリ**を含めると"RDS パフォーマンス カウンター-パフォーマンス モニター"で自分の投稿のタイトル。

一般的な機能のアイデアを参照してください、 [RDS UserVoice ページ](https://aka.ms/uservoice-rds)します。