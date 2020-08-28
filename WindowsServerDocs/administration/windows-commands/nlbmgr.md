---
title: nlbmgr
description: ネットワーク負荷分散マネージャーを使用して、1台のコンピューターからネットワーク負荷分散クラスターとすべてのクラスターホストを構成および管理する際に役立つ、nlbmgr コマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 89cb8590-b7cf-4a27-89fa-0fa62ea1a1ca
author: coreyp-at-msft
ms.author: coreyp
manager: dongill
ms.date: 10/16/2017
ms.openlocfilehash: 5e9036a5fc4a0941445be4c9e9cf11c8064caa08
ms.sourcegitcommit: 96d46c702e7a9c3a321bbbb5284f73911c7baa3c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2020
ms.locfileid: "89023586"
---
# <a name="nlbmgr"></a>nlbmgr

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ネットワーク負荷分散マネージャーを使用して、1台のコンピューターからネットワーク負荷分散クラスターとすべてのクラスターホストを構成および管理します。 また、このコマンドを使用して、クラスター構成を他のホストにレプリケートすることもできます。

コマンドラインからネットワーク負荷分散マネージャーを起動するには、 **systemroot\System32**フォルダーにインストールされているコマンド**nlbmgr.exe**を使用します。

## <a name="syntax"></a>構文

```
nlbmgr [/noping][/hostlist <filename>][/autorefresh <interval>][/help | /?]
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
| --------- | ----------- |
| /noping | ネットワーク負荷分散マネージャが Windows Management Instrumentation (WMI) を使用してホストに接続する前に、ホストに対して ping を実行しないようにします。 使用可能なすべてのネットワークアダプターでインターネット制御メッセージプロトコル (ICMP) を無効にしている場合は、このオプションを使用します。 ネットワーク負荷分散マネージャーが、利用できないホストに接続しようとすると、このオプションを使用すると遅延が発生します。 |
| /hostlist `<filename>` | Filename で指定されたホストをネットワーク負荷分散マネージャーに読み込みます。 |
| /autorefresh `<interval>` | ネットワーク負荷分散マネージャーによって、ホストとクラスターの情報が毎秒更新され `<interval>` ます。 間隔が指定されていない場合、情報は60秒ごとに更新されます。 |
| /? | コマンド プロンプトにヘルプを表示します。 |
| /help | コマンド プロンプトにヘルプを表示します。 |

## <a name="additional-references"></a>その他の参照情報

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [NetworkLoadBalancingClusters コマンドレットリファレンス](/powershell/module/networkloadbalancingclusters)
