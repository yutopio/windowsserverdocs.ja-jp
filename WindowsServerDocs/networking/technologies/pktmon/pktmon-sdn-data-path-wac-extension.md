---
title: Windows 管理センターの SDN データパス診断拡張機能
description: このトピックでは、Windows 管理センターで SDN データパス診断拡張機能を使用してパケットモニターベースのパケットキャプチャを自動化する方法について説明します。
ms.topic: how-to
author: khdownie
ms.author: v-kedow
ms.date: 11/12/2020
ms.openlocfilehash: 9b1a247e0d07a4e44ba7640aa2e95180956ccee8
ms.sourcegitcommit: 8808f871c8cf131f819ef5540286218bd425da96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2020
ms.locfileid: "94632521"
---
# <a name="sdn-data-path-diagnostics-extension-in-windows-admin-center"></a>Windows 管理センターの SDN データパス診断拡張機能

>適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows 10、Azure Stack HCI、Azure Stack Hub、Azure

SDN データパス診断は、さまざまな SDN シナリオに従ったパケットモニターベースのパケットキャプチャを自動化する Windows 管理センターの SDN 監視拡張機能内のツールであり、簡単にフォローおよび操作できる1つのビューで出力を提示します。

## <a name="what-is-packet-monitor-pktmon"></a>パケットモニターの概要 (Pktmon)
パケットモニター (Pktmon) は、Windows 用のインボックスなクロスコンポーネントネットワーク診断ツールです。 パケットキャプチャ、パケット破棄検出、パケットフィルタリング、カウントに使用できます。 このツールは、ネットワークスタック内で可視性を提供するため、コンテナーネットワークや SDN などの仮想化シナリオで特に役立ちます。

## <a name="what-is-windows-admin-center"></a>Windows Admin Center とは?
Windows 管理センターは、ローカルにデプロイされたブラウザーベースの管理ツールであり、Azure またはクラウドの依存関係を持たない Windows Server を管理できます。 Windows Admin Center では、サーバー インフラストラクチャのあらゆる側面を完全に管理できます。特に、インターネットに接続されていないプライベート ネットワークでのサーバーの管理に便利です。 Windows Admin Center は、サーバー マネージャーや MMC などの "インボックス" 管理ツールの進化形です。

## <a name="before-you-start"></a>開始する前に
- このツールを使用するには、対象サーバーで Windows Server 2019 バージョン 1903 (19H1) 以降が実行されている必要があります。
- [Windows 管理センターをインストール](/windows-server/manage/windows-admin-center/deploy/install)します。
- Windows 管理センターにクラスターを追加します。
  1. **[すべての接続]** の下にある **[+ 追加]** をクリックします。
  2. Hyper-Converged クラスター接続を追加することを選択します。
  3. クラスターの名前を入力し、メッセージが表示されたら、使用する資格情報を入力します。
  4. 続行するに **は、ネットワークコントローラーの構成** を確認してください。
  5. ネットワークコントローラーの URI を入力し、[ **検証** ] をクリックします。
  6. [ **追加** ] をクリックして完了します。

クラスターが [接続] の一覧に追加されます。 これをクリックすると、ダッシュボードが起動します。

<center>

:::image type="content" source="media/add-sdn-enabled-hci-connection.png" alt-text="Windows 管理センターで SDN enabled HCI 接続を追加する" border="true":::

</center>

## <a name="getting-started"></a>はじめに

このツールを使用するには、前の手順で作成したクラスターに移動し、"SDN 監視" 拡張機能を選択し、[データパス診断] タブに移動します。

## <a name="selecting-scenarios"></a>シナリオの選択

最初のページには、次の図に示すように、ワークロードのシナリオとインフラストラクチャのシナリオとして分類されたすべての SDN シナリオが一覧表示されます。 開始するには、診断する必要がある SDN シナリオを選択します。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-main-page.png" alt-text="SDN 監視-診断シナリオページ" border="true":::

</center>

## <a name="scenario-parameters"></a>シナリオのパラメーター

シナリオを選択したら、必須パラメーターと省略可能なパラメーターの一覧を入力してキャプチャを開始します。 これらの基本パラメーターによって、診断する必要がある接続がツールによってポイントされます。 このツールでは、これらのパラメーターをクエリに使用して、正常なキャプチャを実行します。ユーザーは、想定されるパケットフロー、シナリオに関係するマシン、クラスター内の場所、各マシンに適用するキャプチャフィルターを確認する必要はありません。 必須パラメーターを使用するとキャプチャを実行でき、オプションのパラメーターを使用すると、ノイズを除外できます。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-scenario-parameters.png" alt-text="SDN 監視-[キャプチャ条件] ページ" border="true":::

</center>

## <a name="capture-log"></a>キャプチャログ

キャプチャを開始すると、キャプチャが開始されているマシンの一覧が拡張機能に表示されます。 資格情報が保存されていない場合は、これらのコンピューターにサインインするように求められることがあります。 診断を試行している ping または問題の再現を開始するには、相対パケットをキャプチャします。 パケットがキャプチャされると、拡張機能によって、パケットがキャプチャされたコンピューターの横にマークが表示されます。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-loading-wheel2.png" alt-text="パケットキャプチャを開始しています" border="true":::

</center>

キャプチャを停止すると、すべてのマシンのログが1ページに表示され、コンピューターのタイトルで割ったものになります。 各タイトルには、仮想マシン (Vm) の場合、コンピューター名、シナリオの役割、およびホストが含まれます。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-log.png" alt-text="キャプチャを停止した後のデータパス診断ログ" border="true":::

</center>

キャプチャされたパケットの主要なパラメーターを示す表に、タイムスタンプ、発信元 IP アドレス、発信元ポート、接続先 IP アドレス、宛先ポート、Ethertype、プロトコル、TCP フラグ、パケットが破棄されたかどうか、および削除の理由が表示されます。

   - これらのパケットのタイムスタンプは、別のページにリダイレクトされるハイパーリンクでもあり、選択したパケットに関する詳細情報を確認できます。 詳細については、以下のセクションを参照してください。
   - 破棄されたすべてのパケットは、ドロップの理由として、ドロップされ **たタブに** "True" の値を持ち、ピンを付けるのが簡単になるように赤いテキストで表示されます。
   - すべてのタブを昇順および降順で並べ替えることができます。
   - 検索バーを使用して、ログ内の任意の列の値を検索できます。
   - [ **再起動** ] ボタンを使用して、選択した同じフィルターを使用してキャプチャを再開できます。

## <a name="details-page"></a>詳細ページ

このページの情報は、ネットワークスタックの各コンポーネントを通過するパケットのフローを調べることができるため、パケットの伝達の問題または不適切な構成の問題がある場合に特に役立ちます。 パケットホップごとに、パケットパラメーターと生パケットの詳細を含む詳細があります。

- ホップは、関連するコンポーネントに基づいてグループ化されます。 各アダプターとその上にあるドライバーは、アダプターの名前でグループ化されます。 これにより、これらのグループタイトルを通じて上位レベルのパケットを簡単に追跡できるようになります。
- すべての破棄されたパケットも赤いテキストで表示されるので、特定しやすくなります。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-details-page.png" alt-text="データパス診断の詳細ページ" border="true":::

</center>

詳細を表示するには、ホップを選択します。 カプセル化と NAT (ネットワークアドレス変換) のシナリオでは、この機能を使用して、ネットワークスタックを通過するパケットの変化を確認し、間違った構成の問題がないかどうかを確認できます。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-details-page-with-pane1.png" alt-text="特定のホップに関する詳細の表示" border="true":::

</center>

下にスクロールして、未加工のパケットの詳細を表示します。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-details-page-with-pane-raw-packet1.png" alt-text="特定のホップに関する生パケットの詳細の表示" border="true":::

</center>

## <a name="display-filters"></a>フィルターの表示

ディスプレイフィルターを使用すると、パケットをキャプチャした後にログをフィルター処理できます。 各フィルターについて、MAC アドレス、IP アドレス、ポート、Ethertype、トランスポートプロトコルなどのパケットパラメーターを指定できます。

   - 表示フィルターでは、IP アドレス、MAC アドレス、およびポートのソースと宛先を区別できます。
   - 表示フィルターは、適用後に削除および編集して、ログの表示を変更することができます。
   - 表示フィルターは、保存されたログでは元に戻されます。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-display-filters.png" alt-text="表示フィルターを使用したログのフィルター処理" border="true":::

</center>

## <a name="save"></a>保存

[保存] ボタンを使用すると、ローカルコンピューターにログを保存して、他のツールを使用した詳細な分析を行うことができます。 保存したログでは、表示フィルターが元に戻されます。 ログは、さまざまな形式で保存できます。

   - Microsoft ネットワークモニターを使用して分析できる ETL 形式。 注: 詳細については、 [このページを確認](pktmon-netmon-support.md) してください。
   - TextAnalysisTool.NET のようなテキストエディターを使用して分析できるテキスト形式。
   - Wireshark などのツールを使用して分析できる pcapng fomat。
      - この変換中、ほとんどのパケットモニターメタデータは失われます。 注: 詳細については、 [このページを確認](pktmon-pcapng-support.md) してください。

<center>

:::image type="content" source="media/sdn-data-path-diagnostics-save.png" alt-text="ログをローカルに保存する" border="true":::

</center>
