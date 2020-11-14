---
title: Pktmon support for Wireshark (pcapng)
description: このトピックでは、Wireshark を使用してパケットモニターで生成された pcapng ログを分析する方法について説明します。
ms.topic: how-to
author: khdownie
ms.author: v-kedow
ms.date: 11/12/2020
ms.openlocfilehash: c65604f6e3f4e87b806513063800ee62d52d1feb
ms.sourcegitcommit: 8808f871c8cf131f819ef5540286218bd425da96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/14/2020
ms.locfileid: "94632509"
---
# <a name="pktmon-support-for-wireshark-pcapng"></a>Pktmon support for Wireshark (pcapng)

>適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows 10、Azure Stack HCI、Azure Stack Hub、Azure

パケットモニター (Pktmon) は、ログを pcapng 形式に変換できます。 これらのログは、Wireshark (または任意の pcapng アナライザー) を使用して分析できます。ただし、重要な情報の一部が pcapng ファイルに存在しない可能性があります。 このトピックでは、予想される出力とその利用方法について説明します。

## <a name="pktmon-pcapng-syntax"></a>Pktmon pcapng 構文

次のコマンドを使用して、pktmon capture を pcapng 形式に変換します。

```powershell
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

## <a name="output-filtering"></a>出力フィルター処理

パケットドロップレポートに関するすべての情報と、ネットワークスタック経由のパケットフローは、pcapng 出力で失われます。 そのため、このような変換については、ログの内容を慎重に事前にフィルター処理する必要があります。 次に例を示します。

- Pcapng 形式では、フローパケットと破棄されたパケットを区別しません。 破棄されたパケットからキャプチャ内のすべてのパケットを分離するには、2つの pcapng ファイルを生成します。1つは、すべてのパケット (" **pktmon pcapng log-capture** ") と、破棄されたパケットのみを含む別のパケット ("pktmon--drop log-drop") を含む1つのパケット (" **--out** ") です。 これにより、削除されたパケットを別のログで分析できます。
- Pcapng 形式では、パケットがキャプチャされた異なるネットワークコンポーネントを区別しません。 このようなマルチレイヤーのシナリオでは、pcapng 出力 "pktmon- **-component-ID 5** " で必要なコンポーネント ID を指定します。 関心のあるコンポーネント Id のセットごとに、このコマンドを繰り返します。
