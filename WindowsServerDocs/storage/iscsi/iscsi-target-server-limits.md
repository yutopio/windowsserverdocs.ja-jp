---
title: iSCSI ターゲットサーバーのスケーラビリティの制限
TOCTitle: iSCSI Target Server Scalability Limits
ms.topic: article
author: JasonGerend
manager: dougkim
ms.author: jgerend
ms.date: 09/11/2018
ms.openlocfilehash: 14ef17f96138c23aeac8e38b93a50b562ca69bba
ms.sourcegitcommit: d08965d64f4a40ac20bc81b14f2d2ea89c48c5c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2020
ms.locfileid: "96865171"
---
# <a name="iscsi-target-server-scalability-limits"></a>iSCSI ターゲットサーバーのスケーラビリティの制限

適用先:Windows Server 2016 では、Windows Server 2012 R2、Windows Server 2012

このトピックでは、Windows Server でサポートされている、テスト済みの Microsoft iSCSI ターゲットサーバーの制限について説明します。 次の表に、テストされたサポートの制限と、適用可能な場合は制限が適用されるかどうかを示します。

## <a name="general-limits"></a>全般的な制限

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>アイテム</p></th>
<th><p>サポートの制限</p></th>
<th><p>リレーションシップ?</p></th>
<th><p>コメント</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>iscsi ターゲットサーバーあたりの iSCSI ターゲットインスタンス</p></td>
<td><p>256</p></td>
<td><p>No</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>iscsi ターゲットサーバーあたりの iSCSI 論理ユニット (Lu) または仮想ディスク</p></td>
<td><p>512</p></td>
<td><p>No</p></td>
<td><p>含まれているテスト構成: ターゲットインスタンスあたりの平均は64ターゲット、256ターゲットインスタンスはターゲットごとに1つの LU を使用します。</p></td>
</tr>
<tr class="odd">
<td><p>iscsi ターゲットインスタンスあたりの iSCSI Lu または仮想ディスク</p></td>
<td><p>256 (Windows Server 2012 の 128)</p></td>
<td><p>Yes</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>ISCSI ターゲットインスタンスに同時に接続できるセッション</p></td>
<td><p>544 (Windows Server 2012 の 512)</p></td>
<td><p>Yes</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>LU あたりのスナップショット数</p></td>
<td><p>512</p></td>
<td><p>Yes</p></td>
<td><p>独立した iSCSI アプリケーションボリュームあたり512のスナップショットの制限があります。</p></td>
</tr>
<tr class="even">
<td><p>ローカルにマウントされた仮想ディスクまたはスナップショット (ストレージアプライアンスあたり)</p></td>
<td><p>32</p></td>
<td><p>はい</p></td>
<td><p>ローカルにマウントされた仮想ディスクは iSCSI 固有の機能を提供&#39;t ではなく、非推奨とされます。詳細については、「 <a href="/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn303411(v=ws.11)">Windows Server 2012 R2 で削除された機能または非推奨の機能</a>」を参照してください。</p></td>
</tr>
</tbody>
</table>

## <a name="fault-tolerance-limits"></a>フォールトトレランスの制限

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>アイテム</p></th>
<th><p>サポートの制限</p></th>
<th><p>リレーションシップ?</p></th>
<th><p>コメント</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>フェールオーバークラスターノード</p></td>
<td><p>8 (Windows Server 2012 では 5)</p></td>
<td><p>No</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>複数のアクティブなクラスターノード</p></td>
<td><p>サポートされています</p></td>
<td>
<p>N/A</p></td>
<td><p>フェールオーバークラスター内の各アクティブノードは、実行可能な所有者ノードとして機能する他のノードと異なる iSCSI ターゲットサーバークラスターインスタンスを所有しています。</p></td>
</tr>
<tr class="odd">
<td><p>エラー回復レベル (ERL)</p></td>
<td><p>0</p></td>
<td><p>はい</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>セッションごとの接続数</p></td>
<td><p>1</p></td>
<td><p>はい</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>ISCSI ターゲットインスタンスに同時に接続できるセッション</p></td>
<td><p>544 (Windows Server 2012 の 512)</p></td>
<td><p>No</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>マルチパス入出力 (MPIO)</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>MPIO パス</p></td>
<td><p>4</p></td>
<td><p>いいえ</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>スタンドアロン iSCSI ターゲットサーバーから、クラスター化された iSCSI ターゲットサーバーへの変換またはその逆の変換</p></td>
<td><p>サポートされていません</p></td>
<td><p>No</p></td>
<td><p>ISCSI ターゲットインスタンスと仮想ディスク構成データ (スナップショットメタデータを含む) は、変換中に失われます。</p></td>
</tr>
</tbody>
</table>

## <a name="network-limits"></a>ネットワークの制限

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>アイテム</p></th>
<th><p>サポートの制限</p></th>
<th><p>リレーションシップ?</p></th>
<th><p>コメント</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>アクティブなネットワークアダプターの最大数</p></td>
<td><p>8</p></td>
<td><p>No</p></td>
<td><p>アプライアンス内のネットワークアダプターの合計数ではなく、iSCSI トラフィック専用のネットワークアダプターに適用されます。</p></td>
</tr>
<tr class="even">
<td><p>サポートされているポータル (IP アドレス)</p></td>
<td><p>64</p></td>
<td><p>はい</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>ネットワークポートの速度</p></td>
<td><p>1 Gbps、10 Gbps、40Gbps、56 Gbps (Windows Server 2012 R2 以降のみ)</p></td>
<td><p>No</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>IPv4</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>IPv6</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>TCP オフロード</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td><p>大規模な送信 (セグメンテーション)、チェックサム、割り込みモデレート、RSS オフロードの活用</p></td>
</tr>
<tr class="odd">
<td><p>iSCSI オフロード</p></td>
<td><p>サポートされていません</p></td>
<td><br/><p>該当なし</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>Jumbo Frame</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>IPSec</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>CRC オフロード</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td></td>
</tr>
</tbody>
</table>

## <a name="iscsi-virtual-disk-limits"></a>iSCSI 仮想ディスクの制限

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>アイテム</p></th>
<th><p>サポートの制限</p></th>
<th><p>リレーションシップ?</p></th>
<th><p>コメント</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>ISCSI イニシエーターから仮想ディスクをベーシックディスクからダイナミックディスクに変換する </p></td>
<td><p>はい</p></td>
<td><p>いいえ</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>仮想ハード ディスク フォーマット</p></td>
<td><p>.vhdx (Windows Server 2012 R2 以降のみ)</p>
<p>.vhd</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>VHD の最小フォーマットサイズ</p></td>
<td><p>.vhdx: 3 MB</p>
<p>.vhd: 8 MB</p></td>
<td><p>Yes</p></td>
<td><p>サポートされているすべての VHD の種類 (親、差分、固定) に適用されます。</p></td>
</tr>
<tr class="even">
<td><p>親 VHD の最大サイズ</p></td>
<td><p>.vhdx:64 TB</p>
<p>.vhd: 2 TB</p></td>
<td><p>Yes</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>VHD の最大サイズを修正</p></td>
<td><p>.vhdx:64 TB</p>
<p>.vhd:16 TB</p></td>
<td><p>Yes</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>差分 VHD の最大サイズ</p></td>
<td><p>.vhdx:64 TB</p>
<p>.vhd: 2 TB</p></td>
<td><p>Yes</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>VHD の固定形式</p></td>
<td><p>サポートされています</p></td>
<td><p>No</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>VHD 差分形式</p></td>
<td><p>サポートされています</p></td>
<td><p>No</p></td>
<td><p>差分 VHD ベースの iSCSI 仮想ディスクを使用してスナップショットを作成することはできません。</p></td>
</tr>
<tr class="odd">
<td><p>親 VHD ごとの差分 Vhd の数</p></td>
<td><p>256</p></td>
<td><p>いいえ (Windows Server 2012 では Yes)</p></td>
<td><p>.Vhdx ファイルの最大サイズは、2レベルの深さ (孫ファイル) です。.vhd ファイルの最大レベルは、1レベルの深さ (子 .vhd ファイル) です。</p></td>
</tr>
<tr class="even">
<td><p>VHD の動的形式</p></td>
<td><p>.vhdx: はい</p>
<p>.vhd: はい (Windows Server 2012 ではいいえ)</p></td>
<td><p>Yes</p></td>
<td><p>マップ解除はサポートされていません&#39;。</p></td>
</tr>
<tr class="odd">
<td><p>exFAT/FAT32/FAT (VHD のホストボリューム)</p></td>
<td><p>サポートされていません</p></td>
<td><p>はい</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>CSV v2</p></td>
<td><p>サポートされていません</p></td>
<td><p>はい</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>ReFS</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>NTFS</p></td>
<td><p>サポートされています</p></td>
<td><p>N/A</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Microsoft 以外の CFS</p></td>
<td><p>サポートされていません</p></td>
<td><p>はい</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>仮想プロビジョニング</p></td>
<td><p>いいえ</p></td>
<td><p>該当なし</p></td>
<td><p>動的 Vhd はサポートされていますが、マップ解除はサポートされていません&#39;。</p></td>
</tr>
<tr class="odd">
<td><p>論理ユニットの圧縮</p></td>
<td><p>はい (Windows Server 2012 R2 以降のみ)</p></td>
<td><p>該当なし</p></td>
<td><p>LUN を圧縮するには、 <a href="/powershell/module/iscsitarget/resize-iscsivirtualdisk">convert-iscsivirtualdisk</a> を使用します。</p></td>
</tr>
<tr class="even">
<td><p>論理ユニットの複製</p></td>
<td><p>サポートされていません</p></td>
<td><p>該当なし</p></td>
<td><p>差分 Vhd を使用して、ディスクデータを迅速に複製できます。</p></td>
</tr>
</tbody>
</table>

## <a name="snapshot-limits"></a>スナップショットの制限

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>アイテム</p></th>
<th><p>サポートの制限</p></th>
<th><p>コメント</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>スナップショットの作成</p></td>
<td><p>サポートされています</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>スナップショットの復元</p></td>
<td><p>サポートされています</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>書き込み可能なスナップショット</p></td>
<td><p>サポートされていません</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>スナップショット–完全に変換</p></td>
<td><p>サポートされていません</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>スナップショット–オンラインロールバック</p></td>
<td><p>サポートされていません</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>スナップショット–書き込み可能に変換</p></td>
<td><p>サポートされていません</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>スナップショット-リダイレクト</p></td>
<td><p>サポートされていません</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>スナップショット-ピン留め</p></td>
<td><p>サポートされていません</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>ローカルマウント</p></td>
<td><p>サポートされています</p></td>
<td><p>ローカルにマウントされた iSCSI 仮想ディスクは非推奨です-詳細については、「 <a href="/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn303411(v=ws.11)">Windows Server 2012 R2 で削除された機能または非推奨の機能</a>」を参照してください。 ダイナミックディスクスナップショットをローカルにマウントすることはできません。</p></td>
</tr>
</tbody>
</table>

## <a name="iscsi-target-server-manageability-and-backup"></a>iSCSI ターゲットサーバーの管理とバックアップ

アプリケーションサーバーから iSCSI 仮想ディスク上のデータのボリュームシャドウコピー (VSS オープンファイルスナップショット) を作成する場合は、または、仮想ディスクサービス (VDS) ハードウェアプロバイダーを必要とする古いアプリケーション (Diskraid コマンドなど) を使用して iSCSI 仮想ディスクを管理する場合は、スナップショットを取得するサーバーに iSCSI ターゲット記憶域プロバイダーをインストールするか、VDS 管理アプリを使用します。

ISCSI ターゲット記憶域プロバイダーは、Windows Server 2016、Windows Server 2012 R2、および Windows Server 2012 の役割サービスです。また、iSCSI ターゲットサーバーが Windows Server 2012 で実行されている限り、次のオペレーティングシステムで [ダウンレベルアプリケーションサーバーの Iscsi ターゲット記憶域プロバイダー (VDS/VSS) を](https://www.microsoft.com/download/details.aspx?id=34759) ダウンロードしてインストールすることもできます。

  - Windows Storage Server 2008 R2

  - Windows Server 2008 R2

  - Windows HPC Server 2008 R2

  - Windows HPC Server 2008

ISCSI ターゲットサーバーが Windows Server 2012 R2 以降を実行しているサーバーでホストされていて、リモートサーバーから VSS または VDS を使用する場合は、リモートサーバーが同じバージョンの Windows Server を実行し、iSCSI ターゲット記憶域プロバイダーの役割サービスがインストールされていることに注意してください。 また、Windows のすべてのバージョンで、iSCSI ターゲット記憶域プロバイダーの役割サービスの1つのバージョンのみをインストールする必要があることに注意してください。

ISCSI ターゲット記憶域プロバイダーの詳細については、「 [Iscsi ターゲット記憶域 (VDS/VSS) プロバイダー](/powershell/module/iscsi/)」を参照してください。

## <a name="tested-compatibility-with-iscsi-initiators"></a>ISCSI イニシエーターとの互換性テスト

次の iSCSI イニシエーターを使用して、iSCSI ターゲットサーバーソフトウェアをテストしました。

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<tbody>
<tr class="odd">
<td><p>Initiator</p></td>
<td><p>Windows Server 2012 R2</p></td>
<td><p>Windows Server 2012</p></td>
<td><p>説明</p></td>
</tr>
<tr class="even">
<td><p>Windows Server 2012 R2</p></td>
<td><p>検証済み</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Windows Server 2012、Windows Server 2008 R2、Windows Server 2008、Windows Server 2003</p></td>
<td><p>検証済み</p></td>
<td><p>検証済み</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>VMWare vSphere 5</p></td>
<td></td>
<td><p>検証済み</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>VMWare ESXi 5.0</p></td>
<td><p>検証済み</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td><p>VMWare ESX 4.1</p></td>
<td><p>検証済み</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>CentOS 6.x</p></td>
<td><p>検証済み</p></td>
<td></td>
<td><p>サイズ変更された仮想ディスクを検出するには、セッションをログアウトしてから再度ログインする必要があります。</p></td>
</tr>
<tr class="even">
<td><p>Red Hat Enterprise Linux 6</p></td>
<td><p>検証済み</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td><p>RedHat Enterprise Linux 5 および5</p></td>
<td><p>検証済み</p></td>
<td><p>検証済み</p></td>
<td></td>
</tr>
<tr class="even">
<td><p>SUSE Linux Enterprise Server 10</p></td>
<td></td>
<td><p>検証済み</p></td>
<td></td>
</tr>
<tr class="odd">
<td><p>Oracle Solaris 2.x</p></td>
<td><p>検証済み</p></td>
<td></td>
<td></td>
</tr>
</tbody>
</table>

また、iSCSI ターゲットサーバーによってホストされる仮想ディスクから、ディスクなしのブートを実行する次の iSCSI イニシエーターをテストしました。

  - Windows Server 2012 R2

  - Windows Server 2012

  - IPXE を使用した PCIe NIC

  - IPXE を使用した CD または USB ディスク

## <a name="additional-references"></a>その他の参照情報

iSCSI ターゲット サーバーと関連テクノロジに関するその他のリソースを次に示します。

- [iSCSI ターゲット ブロック記憶域の概要](iscsi-target-server.md)

- [iSCSI Target Boot Overview](iscsi-boot-overview.md)

- [Windows Server の記憶域](../storage.yml)
