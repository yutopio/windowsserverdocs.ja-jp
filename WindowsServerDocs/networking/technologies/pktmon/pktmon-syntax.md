---
title: Pktmon コマンドの構文と書式設定
description: このページを使用して、Windows Vibranium ビルドの pktmon 構文、コマンド、書式設定、および出力について理解します。
ms.topic: how-to
author: khdownie
ms.author: v-kedow
ms.date: 11/12/2020
ms.openlocfilehash: 3e4c73af3b00f42301b34e59493f25b6d2ccb95c
ms.sourcegitcommit: 8808f871c8cf131f819ef5540286218bd425da96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2020
ms.locfileid: "94632536"
---
# <a name="pktmon-command-syntax-and-formatting"></a>Pktmon コマンドの構文と書式設定

>適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows 10、Azure Stack HCI、Azure Stack Hub、Azure

パケットモニター (Pktmon) は、Windows 用のインボックスなクロスコンポーネントネットワーク診断ツールです。 パケットキャプチャ、パケット破棄検出、パケットフィルタリング、およびカウントに使用できます。 このツールは、ネットワークスタック内で可視性を提供するため、コンテナーネットワークや SDN などの仮想化シナリオで特に役立ちます。 パケットモニターは、Vibranium OS (ビルド 19041) で pktmon.exe コマンドを使用して、ボックスに表示されます。 このトピックでは、pktmon 構文、コマンドの書式設定、および出力について理解する方法について説明します。

## <a name="quick-start"></a>クイック スタート

一般的なシナリオを開始するには、次の手順に従います。

1. キャプチャに必要なパケットの種類 (つまり、特定の IP アドレス、ポート、またはパケットに関連付けられているプロトコル) を特定します。 次に、キャプチャフィルターを適用する構文を確認し、前の手順で特定したパケットのフィルターを適用します。

   ```PowerShell
   C:\Test> pktmon filter add help
   C:\Test> pktmon filter add <filters>
   ```

2. キャプチャを開始し、パケットログを有効にします。

   ```PowerShell
   C:\Test> pktmon start --etw
   ```

3. 診断中の問題を再現します。 予想されるトラフィックがあるかどうかを確認し、トラフィックがコンピューターでどのようにフローされているかを大まかに把握するためのクエリカウンター。

   ```PowerShell
   C:\Test> pktmon counters
   ```

4. 分析用に txt 形式でキャプチャを停止し、ログを取得します。

   ```PowerShell
   C:\Test> pktmon stop
   C:\Test> pktmon format <etl file>
   ```

Txt 出力を分析する方法については、「 [パケットモニターの出力の分析](#analyze-packet-monitor-output) 」を参照してください。

## <a name="capture-filters"></a>キャプチャフィルター

パケットキャプチャを開始する前にフィルターを適用することを強くお勧めします。これは、1つのパケットストリームに集中すると、特定の宛先への接続のトラブルシューティングが容易になるためです。 *すべて* のネットワークトラフィックをキャプチャすると、出力が大きすぎて分析できない可能性があります。 パケットを報告するには、少なくとも1つのフィルターで指定されているすべての条件に一致している必要があります。 最大32のフィルターが同時にサポートされます。

たとえば、次の一連のフィルターでは、または IP アドレス10.0.0.10 との間の ICMP トラフィックと、ポート53のすべてのトラフィックがキャプチャされます。

```PowerShell
C:\Test> pktmon filter add -i 10.0.0.10 -t icmp
C:\Test> pktmon filter add -p 53
```

### <a name="filtering-capability"></a>フィルター機能

- パケットモニターは、MAC アドレス、IP アドレス、ポート、EtherType、トランスポートプロトコル、および VLAN Id によるフィルター処理をサポートしています。 

- MAC アドレス、IP アドレス、またはポートフィルターに関しては、送信元と送信先を区別しません。 

- TCP パケットをさらにフィルター処理するには、一致させる TCP フラグのオプションのリストを指定できます。 サポートされているフラグは、FIN、SYN、RST、PSH、ACK、URG、ECE、および CWR です。

  - たとえば、次のフィルターは、IP アドレス10.0.0.10 によって送受信されたすべての SYN パケットをキャプチャします。

```PowerShell
C:\Test> pktmon filter add -i 10.0.0.10 -t tcp syn
```

- パケットモニターでは、[-e] フラグが任意のフィルターに追加された場合、外側のパケットに加えて、カプセル化された内部パケットにフィルターを適用できます。 サポートされているカプセル化方法は、VXLAN、GRE、NVGRE、および ip アドレスです。 Custom VXLAN port は省略可能で、既定値は4789です。

### <a name="pktmon-filters-syntax"></a>Pktmon filters の構文

```PowerShell
C:\Test> pktmon filter help
pktmon filter { list | add | remove } [OPTIONS | help]

Commands
    list      Display active packet filters.
    add       Add a filter to control which packets are reported.
    remove    Removes all filters.

help
    Show help text for a command.

C:\Test> pktmon filter add help
pktmon filter add <name> [-m mac [mac2]] [-v vlan] [-d { IPv4 | IPv6 | number }]
                         [-t { TCP [flags...] | UDP | ICMP | ICMPv6 | number }]
                         [-i ip [ip2]] [-p port [port2]] [-e [port]]
    Add a filter to control which packets are reported. For a packet to be
    reported, it must match all conditions specified in at least one filter.
    Up to 8 filters can be active at once.

    NOTE1: When two MACs (-m), IPs (-i), or ports (-p) are specified, the filter
           matches packets that contain both. It will not distinguish between source
           or destination for this purpose.

name
    Optional name or description of the filter.

Ethernet frame
    -m, --mac[-address]
        Match source or destination MAC address. See NOTE1 above.

    -v, --vlan
        Match by VLAN Id (VID) in the 802.1Q header.

    -d, --data-link[-protocol], --ethertype
        Match by data link (layer 2) protocol. Can be IPv4, IPv6, ARP, or
        a protocol number.

IP header
    -t, --transport[-protocol], --ip-protocol
        Match by transport (layer 4) protocol. Can be TCP, UDP, ICMP, ICMPv6, or
        a protocol number.
        To further filter TCP packets, an optional list of TCP flags to match can
        be provided. Supported flags are FIN, SYN, RST, PSH, ACK, URG, ECE, and CWR.

    -i, --ip[-address]
        Match source or destination IP address. See NOTE1 above.
        To match by subnet, use CIDR notation with the prefix length.

TCP/UDP header
    -p, --port
        Match source or destination port number. See NOTE1 above.

Encapsulation
    -e, --encap
        This filter also applies to encapsulated inner packets, in addition to the outer
        packet. Supported encapsulation methods are VXLAN, GRE, NVGRE, and IP-in-IP.
        Custom VXLAN port is optional, and defaults to 4789.

Example 1: Ping filter
        pktmon filter add MyPing -i 10.10.10.10 -t ICMP

Example 2: TCP SYN filter for SMB traffic
    pktmon filter add MySmbSyn -i 10.10.10.10 -t TCP SYN -p 445

Example 3: Subnet filter
    pktmon filter add MySubnet -i 10.10.10.0/24
```

## <a name="packet-capture-and-logging"></a>パケットのキャプチャとログ記録

パケットモニターは、パケットログの有無に関係なくネットワークトラフィックをキャプチャできます。 パケットログを使用せずにトラフィックをキャプチャする方法の詳細については、以下の「パケットカウンター」セクションを参照してください。 パケットをキャプチャしてログに記録するには、 **[--etw]** パラメーターを start コマンドに追加します。

**[-C]** パラメーターを使用して監視するコンポーネントを選択します。 すべてのコンポーネント、Nic のみ、またはコンポーネント id の一覧を指定できます。 既定では、すべてのコンポーネントでトラフィックをキャプチャします。 [-D] パラメーターのみを使用して、破棄されたパケットを監視します。 既定では、フローおよび破棄されたパケットをキャプチャします。

たとえば、次のコマンドは、パケットをログに記録せずに、すべてのネットワークアダプターのパケットカウンターをキャプチャします。

```PowerShell
C:\Test> pktmon start -c nics
```

ただし、次のコマンドでは、コンポーネント4と5を通過するドロップされたパケットだけをキャプチャし、ログに記録します。

```PowerShell
C:\Test> pktmon start --etw -c 4,5 -d
```

### <a name="packet-logging-capability"></a>パケットログ機能

- パケットモニターは、複数のログモードをサポートしています。

  - 循環: 最大ファイルサイズに達したときに、新しいパケットによって最も古いものが上書きされます。 これは既定のログモードです。
  - マルチファイル: 最大ファイルサイズに達したときに、新しいログファイルが作成されます。 ログファイルには順番に番号が付けられます (PktMon1、PktMon2 など)。このログモードは、すべてのログを保持するために適用しますが、記憶域の使用率は注意してください。 注: 各ログファイルのファイル作成タイムスタンプは、キャプチャの特定の時間帯を示す値として使用してください。
  - リアルタイム: パケットは、リアルタイムで画面に表示されます。 ログファイルは作成されません。 監視を停止するには、Ctrl + C キーを使用します。
  - メモリ: イベントは、循環メモリバッファーに書き込まれます。 バッファーサイズは、 **[-s]** パラメーターを使用して指定します。 キャプチャを停止した後、バッファーの内容がログファイルに書き込まれます。 このログモードは、非常に雑音の多いシナリオで、非常に短い時間で大量のトラフィックをメモリバッファーにキャプチャする場合に使用します。 他のログモードを使用すると、一部のトラフィックが失われる可能性があります。

- **[-P]** パラメーターを使用してログに記録するパケットの量を指定します。 そのパラメーターを0に設定して、サイズに関係なくすべてのパケットのパケット全体をログに記録します。 既定値は128バイトで、ほとんどのパケットのヘッダーを含める必要があります。

- **[-S]** パラメーターを使用して、ログファイルのサイズを指定します。 これは、循環ログモードでのファイルの最大サイズになります。これにより、パケットモニターは古いパケットを新しいもので上書きします。 これは、マルチファイルログモードでの各ファイルの最大サイズにもなります。これにより、パケットモニタは次のパケットをログに記録するために新しいファイルを作成します。 このパラメーターを使用して、メモリログモードのバッファーサイズを設定することもできます。

### <a name="pktmon-start-syntax"></a>Pktmon の開始構文

```PowerShell
C:\Test> pktmon start help
pktmon start [-c { all | nics | [ids...] }] [-d] [--etw [-p size] [-k keywords]]
             [-f] [-s] [--log-mode {circular | multi-file | real-time | memory}]
    Start packet monitoring.

-c, --components
    Select components to monitor. Can be all components, NICs only, or a
    list of component ids. Defaults to all.

-d, --drop-only
    Only report dropped packets. By default, successful packet propagation
    is reported as well.

ETW Logging
    --etw
        Start a logging session for packet capture.

    -p, --packet-size
        Number of bytes to log from each packet. To always log the entire
        packet, set this to 0. Default is 128 bytes.

    -k, --keywords
        Hexadecimal bitmask (i.e. sum of the below flags) that controls
        which events are logged. Default is 0x012.

        Flags:
        0x001 - Internal Packet Monitor errors.
        0x002 - Information about components, counters and filters.
                This information is added to the end of the log file.
        0x004 - Source and destination information for the first
                packet in NET_BUFFER_LIST group.
        0x008 - Select packet metadata from NDIS_NET_BUFFER_LIST_INFO
                enumeration.
        0x010 - Raw packet, truncated to the size specified in
                [--packet-size] parameter.

    -f, --file-name
        .etl log file. Default is PktMon.etl.

    -s, --file-size
        Maximum log file size in megabytes. Default is 512 MB.

    -l, --log-mode
        Select logging mode. Default is circular.

        circular
            New events overwrite the oldest ones when
            when the maximum file size is reached.

        multi-file
            A new log file is created when the maximum file size is reached.
            Log files are sequentially numbered. PktMon1.etl, PktMon2.etl, etc.

        real-time
            Display events and packets on screen at real time. No log file is created.
            Press Ctrl+C to stop monitoring.

        memory
            Events are written to a circular memory buffer.
            Buffer size is specified in [--file-size] parameter.
            Buffer contents is written to a log file during stop operation.

Example: pktmon start --etw -l real-time
```

## <a name="packet-analysis-and-formatting"></a>パケット分析と書式設定

パケットモニターは、ETL 形式でログファイルを生成します。 分析用に ETL ファイルをフォーマットするには、次のような複数の方法があります。

- ログをテキスト形式に変換し (既定のオプション)、TextAnalysisTool.NET などのテキストエディターツールを使用して分析します。 パケットデータは TCPDump 形式で表示されます。 次のガイドに従って、テキストファイル内の出力を分析する方法を確認してください。
- [Wireshark](pktmon-pcapng-support.md)を使用してログを分析するように、ログを pcapng 形式に変換します。*
- [ネットワークモニター](pktmon-netmon-support.md)で ETL ファイルを開きます。*

>[!NOTE]
>* 上記のハイパーリンクを使用して、 **Wireshark** と **ネットワークモニター** のパケットモニターのログを解析および分析する方法を確認してください。

### <a name="pktmon-format-syntax"></a>Pktmon format 構文

```PowerShell
C:\Test> pktmon format help
pktmon format log.etl [-o log.txt] [-b] [-v [level]] [-x] [-e] [-l [port]
    Convert log file to text format.

-o, --out
    Name of the formatted text file.

-s, --stats-only
    Display log file statistical information.

Network packet formatting options

    -b, --brief
        Abbreviated packet format.

    -v, --verbose
        Verbosity level [1..3].

    -x, --hex
        Hexadecimal format.

    -e, --no-ethernet
        Don't print ethernet header.

    -l, --vxlan
        Custom VXLAN port.


Example: pktmon format C:\tmp\PktMon.etl

C:\Test> pktmon pcapng help
pktmon pcapng log.etl [-o log.pcapng]
    Convert log file to pcapng format.
    Dropped packets are not included by default.

-o, --out
    Name of the formatted pcapng file.

-d, --drop-only
    Convert dropped packets only.

-c, --component-id
    Filter packets by a specific component ID.

Example: pktmon pcapng C:\tmp\PktMon.etl -d -c nics
```

### <a name="analyze-packet-monitor-output"></a>パケットモニターの出力の分析

パケットモニターは、ネットワークスタックの各コンポーネントによって、パケットのスナップショットをキャプチャします。 これにより、各パケットの複数のスナップショットが存在することになります (下の図では、青いボックスが線で示されています)。
これらの各パケットスナップショットは、2つの行 (赤と緑のボックス) で表されます。 タイムスタンプで始まるパケットインスタンスに関するデータを含む行が少なくとも1行あります。 の直後には、解析された未加工パケットがテキスト形式 (タイムスタンプなし) で表示されるように、少なくとも1行 (下の図で太字) があります。パケットがカプセル化されている場合、緑色のボックスにパケットのように複数の行が存在する可能性があります。

<center>

:::image type="content" source="media/pktmon-log-example.png" alt-text="パケットモニターの txt ログ出力の例" border="false":::

</center>

同じパケットのすべてのスナップショットを関連付けるには、PktGroupId と PktNumber の値 (黄色で強調表示されています) を監視します。同じパケットのすべてのスナップショットは、これらの2つの値を共通に持つ必要があります。 外観の値 (青で強調表示されています) は、同じパケットの後続のスナップショットごとにカウンターとして機能します。 たとえば、パケットの最初のスナップショット (パケットが最初にネットワークスタックに表示された場所) の値が1である場合、次のスナップショットの値は2になります。

各パケットスナップショットには、スナップショットに関連付けられているコンポーネントを示すコンポーネント id (上の画像で下線が引かれています) があります。 コンポーネント名とパラメーターを解決するには、ログファイルの下部にある [コンポーネント] ボックスの一覧でこのコンポーネント id を検索します。 次の図は、[コンポーネント 1] が黄色で強調表示されている部分を示しています (これは、上記の最後のスナップショットがキャプチャされたコンポーネントです)。
2つのエッジを持つコンポーネントでは、各エッジに2つのスナップショット (上の図のように、外観3と外観4のスナップショット) がレポートされます。

各ログファイルの下部には、次の図のようにフィルター一覧が表示されます (青色で強調表示されています)。 各フィルターには、指定されたパラメーター (下記の例のプロトコル ICMP) と残りのパラメーターの0が表示されます。

<center>

:::image type="content" source="media/pktmon-log-example-components.png" alt-text="パケットモニターの txt ログ出力コンポーネントの例":::

</center>

破棄されたパケットの場合は、パケットがドロップされたスナップショットを表す行の前に "drop" という単語が表示されます。 削除された各パケットは、値を指定することもできます。 このパラメーターは、パケット破棄の理由について簡単に説明します。たとえば、MTU の不一致、フィルター処理された VLAN などです。

<center>

:::image type="content" source="media/dropped-packet-log-example.png" alt-text="破棄されたパケットログの例":::

</center>

## <a name="packet-counters"></a>パケット カウンター

パケットモニターカウンターは、ネットワークスタック全体のネットワークトラフィックの概要を示します。ログを分析する必要はありません。これは、コストのかかるプロセスです。 パケットモニターのキャプチャを開始した後、 **pktmon カウンター** を使用してパケットカウンターを照会することで、トラフィックパターンを調べます。 **Pktmon reset** を使用してカウンターを0にリセットするか、 **pktmon stop** を使用してすべての監視を停止します。

- カウンターは、上部のネットワークアダプターと一番下のプロトコルにバインドされています。
- Tx/Rx: カウンターは、送信 (Tx) と受信 (Rx) の両方向の2つの列に分けられます。  
- エッジ: コンポーネントは、パケットがコンポーネントの境界 (エッジ) を越えたときにパケット伝達を報告します。 各コンポーネントには1つ以上のエッジが含まれる場合があります。 ミニポートドライバーは、通常、上端が1つで、プロトコルが1つの下端を持ち、フィルタードライバーの上端と下端があります。  
- 削除: パケットドロップカウンターは同じテーブルで報告されています。

次の例では、新しいキャプチャが開始され、 **pktmon カウンタ** コマンドを使用してカウンターがキャプチャされる前にクエリが実行されました。 このカウンターは、ネットワークスタックから送信される1つのパケットを示しています。これは、プロトコル層から物理ネットワークアダプターまでのすべての方法で、もう一方の方向に応答が返されます。 Ping または応答がない場合は、カウンターを使用してこれを簡単に検出できます。

<center>

:::image type="content" source="media/pktmon-counters-with-perfect-flow.png" alt-text="完全なフローを備えたパケットカウンターの例" border="false":::

</center>

次の例では、[カウンター] 列の下にドロップが表示されます。 **Pktmon カウンター--json** を使用して json 形式のカウンターデータを要求することによって、各コンポーネントの最後の削除理由を取得します。または、出力ログを分析して詳細情報を取得します。

<center>

:::image type="content" source="media/pktmon-counters-drop-example.png" alt-text="パケットが破棄されたパケットカウンターの例" border="false":::

</center>

これらの例に示されているように、カウンターでは、簡単に分析できる図を通じて多数の情報が提供される可能性があります。

### <a name="pktmon-counters-syntax"></a>Pktmon カウンターの構文

```PowerShell
C:\Test> pktmon counters help
pktmon [comp] counters [-t { all | drop | flow }] [-z] [--json]
    Display current per-component counters.

-t, --counter-type
    Select which types of counters to show.
    Supported values are all counters (default), drops only, or flows only.

-z, --show-zeros
    Show counters that are zero in both directions.

-i, --show-hidden
    Show components that are hidden by default.

--json
    Output the counters in JSON format.
```

## <a name="networking-stack-layout"></a>ネットワークスタックのレイアウト

コマンド **pktmon の一覧** を使用して、ネットワークスタックのレイアウトを確認します。

:::image type="content" source="media/pktmon-networking-stack-example.png" alt-text="ネットワークスタックのレイアウトの例" border="false":::

コマンドは、アダプターのバインドによって配置されたネットワークコンポーネント (ドライバー) を示します。

一般的なバインディングは、次の要素で構成されます。

- 単一のネットワークインターフェイスカード (NIC)
- 少数の (おそらくゼロの) フィルタードライバー
- 1つまたは複数のプロトコルドライバー (TCP/IP またはその他)

各コンポーネントは、監視用に個々のコンポーネントを対象とするために使用される、パケットモニターコンポーネント ID によって一意に識別されます。

>[!NOTE]
>Id は永続的ではなく、再起動の間に変更される可能性があり、パケットモニターのドライバーが再起動されます。

### <a name="pktmon-list-syntax"></a>Pktmon list 構文

```powershell
C:\Test> pktmon list help
pktmon [comp] list
    List all active components.

-i, --show-hidden
    Show components that are hidden by default.

--json
    Output the list in JSON format.
```