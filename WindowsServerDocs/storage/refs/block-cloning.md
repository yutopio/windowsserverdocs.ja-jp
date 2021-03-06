---
description: 詳細については、「ReFS での複製のブロック」を参照してください。
ms.assetid: fd427da3-3869-428f-bf2a-56c4b7d99b40
title: ReFS でのブロックの複製
author: gawatu
ms.author: gawatu
manager: gawatu
ms.date: 10/17/2018
ms.topic: article
ms.openlocfilehash: c73f6bde78011e2244ce857b52ed3cbe97abe8ff
ms.sourcegitcommit: 65b6de6b44d41f1180c45db11cdd60cb2a093b46
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2020
ms.locfileid: "97041271"
---
# <a name="block-cloning-on-refs"></a>ReFS でのブロックの複製

>適用先:Windows Server 2019、Windows Server 2016、Windows Server (半期チャネル)

ブロックの複製によって、アプリケーションの代わりにファイル システムが一定範囲のファイル サイズに応じたファイルのコピーを実行します。この際、コピー先のファイルをコピー元のファイルと同じにしたり、別のファイルにしたりすることができます。 残念ながら、コピー操作にはコストがかかります。これは、コピー操作によって、コストがかかる読み取りや書き込みが基になる物理データに対してトリガーされるためです。

ただし ReFS のブロックの複製では、ファイル データに対して読み取りや書き込みが実行されるのではなく、低コストのメタデータ操作としてコピーが実行されます。 ReFS を使用すると、複数のファイルが同じ論理クラスター (ボリューム上の物理的な場所) を共有することが可能になるため、コピー操作では、ファイルの領域を個別の物理的な場所に再マップすることだけが必要となります。これにより、コストがかかる物理的な操作ではなく、すばやい論理操作が実行されることになります。 ブロックの複製を利用すると、操作は短時間で完了し、基になる記憶域に対する I/O の数が減少します。 こうしたパフォーマンスの向上により、ブロックの複製操作を使用したときに、.vhdx チェックポイントのマージ操作が大幅に高速化されるため、仮想化ワークロードでもメリットが生じます。 また、複数のファイルが同じ論理クラスターを共有できるため、同一のデータが複数回物理的に格納されることがなくなり、記憶域容量が節約されます。

## <a name="how-it-works"></a>しくみ

ReFS のブロックの複製では、ファイル データの操作ではなくメタデータ操作が実行されます。 この最適化を実現するために、ReFS では、コピー元の領域のメタデータに対して参照カウントが採用されています。 この参照カウントは、同じ物理領域を参照する個々のファイル領域の数を記録します。 これにより、複数のファイルが同じ物理データを共有できるようになります。

![複数のファイルが同じ領域を参照する場合の参照カウントの更新状況](media/ref-count-example.gif)

論理クラスターごとに参照カウントを保持するため、ReFS では、ファイル間の分離が維持されます。また、共有領域への書き込みによって書き込み時割り当て (Allocate-on-Write) メカニズムがトリガーされ、ReFS では、受け入れた書き込みに対して新しい領域が割り当てられます。 このメカニズムは、共有されている論理クラスターの整合性を保持します。

### <a name="example"></a>例
2 つのファイル、X と Y があるとします。各ファイルは 3 つの領域で構成されており、各領域は個別の論理クラスターにマップされています。

![3 つの個別の領域で構成される 2 つのファイル。すべての領域は、参照カウントが 1 となっている領域にマップされています。](media/block-clone-1.png)

ここで、アプリケーションが、ファイル X からファイル Y に対してブロックの複製操作を実行したとします。この操作では、領域 A と B は、領域 E のオフセットにコピーされます。その結果、ファイル システムでは次のような状態になります。

![ブロックの複製が行われた領域に対して参照カウントが 2 を示しています](media/block-clone-2.png)

このファイル システムの状態では、ブロックの複製の対象となった領域が適切に複製されていることが示されています。 ReFS では、このコピー操作を実行するときに VCN から LCN へのマッピングの更新のみが行われるため、物理データの読み取りや、ファイル Y に含まれる物理データの上書きは実行されません。 現在、ファイル X と Y は論理クラスターを共有しています。このことは、表の参照カウントに示されています。 データが物理的にコピーされないため、ReFS ではボリューム上の容量の消費量が削減されます。

次に、アプリケーションがファイル X に含まれる領域 A の上書きを実行したとします。ReFS では、共有領域が複製され、参照カウントが適切に更新され、新しく複製された領域へ受け入れる書き込みが実行されます。 これにより、ファイル間の分離が維持されます。

![新しい領域 G への書き込みと参照カウントの更新によって維持される分離](media/block-clone-3.png)

書き込みを変更した後でも、領域 B は両方のファイルによって共有されています。 領域 A がクラスターよりも大きい場合、変更されたクラスターのみが複製され、残りの部分は共有されたままになることに注意してください。


## <a name="functionality-restrictions-and-remarks"></a>機能に関する制限と注意事項
- コピー元とコピー先の領域は、クラスターの境界で始まり、クラスターの境界で終了する必要があります。
- 複製される領域は、4 GB 未満の長さにする必要があります。
- 同じ物理領域にマップできるファイル領域の最大数は、8175 個です。
- コピー先の領域は、ファイルの終わりを超えて拡張しないでしてください。 アプリケーションで複製されるデータのコピー先を拡張する必要がある場合は、最初に [SetEndOfFile](/windows/win32/api/fileapi/nf-fileapi-setendoffile) を呼び出す必要があります。
- コピー元とコピー先の領域が同じファイルに含まれている場合、それらの領域は重複してコピーされません  (場合によっては、ブロックの複製操作を、重複を回避する複数のブロックの複製に分割することによって、アプリケーションを続行することができます)。
- コピー元とコピー先のファイルは、同じ ReFS ボリューム上にある必要があります。
- コピー元とコピー先のファイルは、[整合性ストリーム](/windows/win32/fileio/file-attribute-constants)の設定が同じになっている必要があります。
- コピー元のファイルがスパース ファイルである場合は、コピー先のファイルもスパース ファイルであることが必要です。
- ブロックの複製操作では、共有されている便宜的ロック ([レベル 2 の便宜的ロック](/windows/win32/fileio/types-of-opportunistic-locks)とも呼ばれています) が動作しなくなります。
- ReFS ボリュームは、Windows Server 2016 でフォーマットされている必要があります。フェールオーバー クラスタリングを使用している場合は、フォーマット時にクラスタリングの機能レベルが Windows Server 2016 以降になっている必要があります。

## <a name="additional-references"></a>その他の参照情報

-   [ReFS の概要](refs-overview.md)
-   [ReFS 整合性ストリーム](integrity-streams.md)
-   [記憶域スペース ダイレクトの概要](../storage-spaces/storage-spaces-direct-overview.md)
-   [DUPLICATE_EXTENTS_DATA](/windows/win32/api/winioctl/ns-winioctl-duplicate_extents_data)
-   [FSCTL_DUPLICATE_EXTENTS_TO_FILE](/windows/win32/api/winioctl/ni-winioctl-fsctl_duplicate_extents_to_file)
