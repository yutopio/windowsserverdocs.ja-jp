---
description: 詳細については、記憶域スペースダイレクトのドライブ対称の考慮事項に関するページを参照してください。
title: 記憶域スペースダイレクトの対称に関する考慮事項
ms.author: cosdar
manager: eldenc
ms.topic: article
author: cosmosdarwin
ms.date: 10/08/2018
ms.localizationpriority: medium
ms.openlocfilehash: 38ab78f24e6900019a134b480ce477b45ca5ff0e
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97039390"
---
# <a name="drive-symmetry-considerations-for-storage-spaces-direct"></a>記憶域スペースダイレクトの対称に関する考慮事項

> 適用先:Windows Server 2019、Windows Server 2016

[記憶域スペースダイレクト](storage-spaces-direct-overview.md) は、すべてのサーバーにまったく同じドライブがある場合に最適です。

実際、これは常に実用的ではないということを認識しています。記憶域スペースダイレクトは、長年にわたって実行するように設計されており、組織のニーズの拡大に合わせて拡張できます。 現在、spacious 3 TB のハードドライブを購入できます。来年には、小規模なものを見つけることができなくなる可能性があります。 そのため、いくつかの混合と一致がサポートされています。

このトピックでは、その制約について説明し、サポート対象およびサポート対象外の構成の例を示します。

## <a name="constraints"></a>制約

### <a name="type"></a>種類

すべてのサーバーは、[ドライブの種類](choosing-drives.md#drive-types)が同じである必要があります。

たとえば、1 台のサーバーに NVMe が存在する場合は、"*すべて*" に NVMe が存在する必要があります。

### <a name="number"></a>Number

すべてのサーバーは、種類別のドライブの数が同じである必要があります。

たとえば、1 台のサーバーに 6 台の SSD が存在する場合は、"*すべて*" に 6 台の SSD が存在する必要があります。

   > [!NOTE]
   > 障害発生時またはドライブの追加や削除時に、ドライブ数が一時的に異なることはかまいません。

### <a name="model"></a>モデル

可能な限り、同じモデルおよびファームウェアのバージョンのドライブを使用することをお勧めします。 できない場合は、可能な限り類似するドライブを慎重に選択してください。 記憶域スペースダイレクトは IO を均等に分散し、モデルに基づいて区別されないため、同じ種類の同じ種類のドライブを混在させても、パフォーマンスや耐久性が向上しないようにすることをお勧めします。

   > [!NOTE]
   > 類似の SATA と SAS のドライブを組み合わせることはかまいません。

### <a name="size"></a>サイズ

可能な限り、同じサイズのドライブを使用することをお勧めします。 サイズが異なる容量ドライブを使用すると、一部の容量が使用できなくなる場合があり、サイズが異なるキャッシュ ドライブを使用すると、キャッシュのパフォーマンスが向上しない場合があります。 詳細については、次のセクションを参照してください。

   > [!WARNING]
   > サーバー間で容量ドライブのサイズが異なると、容量が残される可能性があります。

## <a name="understand-capacity-imbalance"></a>理解: 容量の不均衡

記憶域スペースダイレクトは、複数のドライブやサーバーにわたる容量の不均衡に対する堅牢性を備えています。 不均衡が深刻な場合でも、すべてが継続して機能します。 ただし、いくつかの要因によっては、すべてのサーバーでは使用できない容量については、使用できなくなる場合があります。

これが発生する理由を確認するために、次の簡略化された図で検討します。 色付きのボックスはそれぞれ、ミラー化されたデータの 1 つのコピーを表します。 たとえば、A、A'、A'' とマークされているボックスは、同じデータの 3 つのコピーです。 サーバーのフォールト トレランスを利用するには、これらのコピーを異なるサーバーに格納する *必要があります*。

### <a name="stranded-capacity"></a>残される容量

図に示すように、サーバー 1 (10 TB) とサーバー 2 (10 TB) はいっぱいです。 サーバー 3 には大きいドライブがあるため、その合計容量はより大きいです (15 TB)。 ただし、サーバー 3 にさらに多くの 3 方向ミラー データを格納するには、既にいっぱいになっているサーバー 1 とサーバー 2 にもコピーが必要になります。 サーバー 3 の残りの 5 TB 容量は使用できません。これが *"残される"* 容量です。

![3 方向ミラー、3 台のサーバー、残される容量](media/drive-symmetry-considerations/Size-Asymmetry-3N-Stranded.png)

### <a name="optimal-placement"></a>最適な配置

逆に、3 方向ミラーの回復性を備えた 10 TB、10 TB、10 TB、15 TB の容量の 4 台のサーバーでは、図に示すように、使用可能なすべての容量を使用するような方法でコピーを有効に配置 *できます*。 これが可能である場合は常に、記憶域スペース ダイレクト アロケーターは最適な配置を見つけて使用するので、残される容量がありません。

![3 方向ミラー、4 台のサーバー、残される容量なし](media/drive-symmetry-considerations/Size-Asymmetry-4N-No-Stranded.png)

サーバーの数、回復性、容量の不均衡の深刻度、およびその他の要因は、残される容量があるかどうかに影響します。 **最も賢明で一般的な規則は、すべてのサーバーで使用できる容量のみが使用可能であることが保証されると想定することです。**

## <a name="understand-cache-imbalance"></a>理解: キャッシュの不均衡

記憶域スペースダイレクトは、複数のドライブやサーバーにまたがるキャッシュの不均衡に対して堅牢です。 不均衡が深刻な場合でも、すべてが継続して機能します。 さらに、記憶域スペースダイレクトは常に使用可能なすべてのキャッシュを使用します。

ただし、異なるサイズのキャッシュ ドライブを使用すると、キャッシュのパフォーマンスの向上が一様にも予測どおりにもならない場合があります。キャッシュ ドライブが大きい[ドライブのバインド](understand-the-cache.md#server-side-architecture)への IO のみがパフォーマンスの向上を示す可能性があります。 記憶域スペースダイレクトは、IO をバインド間で均等に分散し、キャッシュから容量への比率に基づいては区別しません。

![キャッシュの不均衡](media/drive-symmetry-considerations/Cache-Asymmetry.png)

   > [!TIP]
   > キャッシュ バインドの詳細については、[キャッシュの概要](understand-the-cache.md)に関する記事を参照してください。

## <a name="example-configurations"></a>構成例

サポート対象およびサポート対象外の構成を次に示します。

### <a name="supported-supported-different-models-between-servers"></a>![サポート対象](media/drive-symmetry-considerations/supported.png) サポート対象: サーバー間で異なるモデル

最初の 2 台のサーバーでは、NVMe モデル "X" が使用されていますが、3 台目のサーバーでは、非常に類似する NVMe モデル "Z" が使用されています。

| サーバー 1                    | サーバー 2                    | サーバー 3                    |
|-----------------------------|-----------------------------|-----------------------------|
| 2 台 x NVMe モデル X (キャッシュ)    | 2 台 x NVMe モデル X (キャッシュ)    | 2 台 x NVMe モデル Z (キャッシュ)    |
| 10 台 x SSD モデル Y (容量) | 10 台 x SSD モデル Y (容量) | 10 台 x SSD モデル Y (容量) |

これはサポートされています。

### <a name="supported-supported-different-models-within-server"></a>![サポート対象](media/drive-symmetry-considerations/supported.png) サポート対象: サーバー内で異なるモデル

すべてのサーバーで、非常に類似する HDD モデル "Y" と "Z" の異なる組み合わせが使用されています。 どのサーバーにも合計 10 台の HDD があります。

| サーバー 1                   | サーバー 2                   | サーバー 3                   |
|----------------------------|----------------------------|----------------------------|
| 2 台 x SDD モデル X (キャッシュ)    | 2 台 x SDD モデル X (キャッシュ)    | 2 台 x SDD モデル X (キャッシュ)    |
| 7 台 x HDD モデル Y (容量) | 5 台 x HDD モデル Y (容量) | 1 台 x HDD モデル Y (容量) |
| 3 台 x HDD モデル Z (容量) | 5 台 x HDD モデル Z (容量) | 9 台 x HDD モデル Z (容量) |

これはサポートされています。

### <a name="supported-supported-different-sizes-across-servers"></a>![サポート対象](media/drive-symmetry-considerations/supported.png) サポート対象: サーバー間で異なるサイズ

最初の 2 台のサーバーでは 4 TB の HDD が使用されていますが、3 台目のサーバーでは非常に類似した 6 TB の HDD が使用されています。

| サーバー 1                | サーバー 2                | サーバー 3                |
|-------------------------|-------------------------|-------------------------|
| 2 台 x 800 GB NVMe (キャッシュ) | 2 台 x 800 GB NVMe (キャッシュ) | 2 台 x 800 GB NVMe (キャッシュ) |
| 4 台 x 4 TB HDD (容量) | 4 台 x 4 TB HDD (容量) | 4 台 x 6 TB HDD (容量) |

これはサポートされていますが、残される容量が発生します。

### <a name="supported-supported-different-sizes-within-server"></a>![サポート対象](media/drive-symmetry-considerations/supported.png) サポート対象: サーバー内で異なるサイズ

すべてのサーバーで、1.2 TB の SSD と、非常に類似する 1.6 TB SSD の異なる組み合わせが使用されています。 どのサーバーにも合計 4 台の SSD があります。

| サーバー 1                 | サーバー 2                 | サーバー 3                 |
|--------------------------|--------------------------|--------------------------|
| 3 台 x 1.2 TB SSD (キャッシュ)   | 2 台 x 1.2 TB SSD (キャッシュ)   | 4 台 x 1.2 TB SSD (キャッシュ)   |
| 1 台 x 1.6 TB SSD (キャッシュ)   | 2 台 x 1.6 TB SSD (キャッシュ)   | -                        |
| 20 台 x 4 TB HDD (容量) | 20 台 x 4 TB HDD (容量) | 20 台 x 4 TB HDD (容量) |

これはサポートされています。

### <a name="unsupported-not-supported-different-types-of-drives-across-servers"></a>![サポートされていない](media/drive-symmetry-considerations/unsupported.png) サポート対象外: サーバー間で異なる種類のドライブ

サーバー 1 には NVMe が存在しますが、他のサーバーには存在しません。

| サーバー 1            | サーバー 2            | サーバー 3            |
|---------------------|---------------------|---------------------|
| 6 台 x NVMe (キャッシュ)    | -                   | -                   |
| -                   | 6 台 x SSD (キャッシュ)     | 6 台 x SSD (キャッシュ)     |
| 18 台 x HDD (容量) | 18 台 x HDD (容量) | 18 台 x HDD (容量) |

これはサポートされていません。 ドライブの種類は、すべてのサーバーで同じである必要があります。

### <a name="unsupported-not-supported-different-number-of-each-type-across-servers"></a>![サポートされていない](media/drive-symmetry-considerations/unsupported.png) サポート対象外: サーバー間で種類別の数が異なる

サーバー 3 には他より多くのドライブがあります。

| サーバー 1            | サーバー 2            | サーバー 3            |
|---------------------|---------------------|---------------------|
| 2 台 x NVMe (キャッシュ)    | 2 台 x NVMe (キャッシュ)    | 4 台 x NVMe (キャッシュ)    |
| 10 台 x HDD (容量) | 10 台 x HDD (容量) | 20 台 x HDD (容量) |

これはサポートされていません。 種類別のドライブの数は、すべてのサーバーで同じである必要があります。

### <a name="unsupported-not-supported-only-hdd-drives"></a>![サポートされていない](media/drive-symmetry-considerations/unsupported.png) サポート対象外: HDD ドライブのみ

すべてのサーバーに HDD ドライブのみが接続されています。

|サーバー 1|サーバー 2|サーバー 3|
|-|-|-|
|18 台 x HDD (容量) |18 台 x HDD (容量)|18 台 x HDD (容量)|

これはサポートされていません。 各サーバーに接続されている 2 台以上のキャッシュ ドライブ (NvME または SSD) を追加する必要があります。

## <a name="summary"></a>まとめ

要約すると、クラスター内のすべてのサーバーには同じ種類のドライブが存在し、種類別の数が同じである必要があります。 上記の考慮事項を使用して、必要に応じてドライブ モデルとドライブ サイズをうまく組み合わせることがサポートされています。

| 制約 | State |
|--|--|
| すべてのサーバーで同じ種類のドライブ | **必須** |
| すべてのサーバーで種類別の数が同じ | **必須** |
| すべてのサーバーで同じドライブ モデル | 推奨 |
| すべてのサーバーで同じドライブ サイズ | 推奨 |

## <a name="additional-references"></a>その他の参照情報

- [記憶域スペース ダイレクトのハードウェア要件](storage-spaces-direct-hardware-requirements.md)
- [記憶域スペース ダイレクトの概要](storage-spaces-direct-overview.md)
