---
title: verifier
description: Driver Verifier マネージャーユーティリティを実行するベリファイアコマンドのリファレンス記事です。
ms.topic: reference
ms.assetid: 782173d6-f196-4bc4-a547-76109829453c
ms.author: lizross
author: eross-msft
manager: mtillman
ms.date: 10/16/2017
ms.openlocfilehash: df3a9826463ea4062fb661e04e8fb774275c09d7
ms.sourcegitcommit: f45640cf4fda621b71593c63517cfdb983d1dc6a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92156263"
---
# <a name="verifier"></a>verifier

> 適用対象: Windows Server (半期チャネル)、Windows Server 2019、Windows Server 2016、Windows Server 2012 R2、Windows Server 2012

ドライバーの検証ツールは、Windows カーネルモード ドライバーとグラフィックス ドライバーを監視して、無効な関数呼び出しやシステムを破損する可能性があるアクションを検出します。 ドライバーの検証ツールは、Windows ドライバーにさまざまなストレスを適用し、不適切な動作を検出するためのテストを行います。 実行するテストを構成できます。これにより、高負荷の負荷によってドライバーを配置したり、より効率的なテストを行ったりすることができます。 また、複数のドライバーで同時に、または一度に1つのドライバーに対して、ドライバーの検証ツールを実行することもできます。

> [!IMPORTANT]
> ドライバーの検証ツールを使用するには、コンピューターの Administrators グループにいる必要があります。
> ドライバーの検証ツールを実行すると、コンピューターがクラッシュする可能性があるため、このユーティリティはテストおよびデバッグに使用するコンピューターでのみ実行してください。

## <a name="syntax"></a>構文

```
verifier /standard /all
verifier /standard /driver NAME [NAME ...]
verifier /flags <options> /all
verifier /flags <options> /driver NAME [NAME ...]
verifier /rules [OPTION ...]
verifier /query
verifier /querysettings
verifier /bootmode [persistent | disableafterfail | oneboot]
verifier /reset
verifier /faults [Probability] [PoolTags] [Applications] [DelayMins]
verifier /faultssystematic [OPTION ...]
verifier /log LOG_FILE_NAME [/interval SECONDS]
verifier /volatile /flags <options>
verifier /volatile /adddriver NAME [NAME ...]
verifier /volatile /removedriver NAME [NAME ...]
verifier /volatile /faults [Probability] [PoolTags] [Applications] [DelayMins]
verifier /domain <types> <options> /driver ... [/logging | /livedump]
verifier /logging
verifier /livedump
verifier /?
verifier /help
```

### <a name="parameters"></a>パラメーター

| パラメーター | 説明 |
|--|--|
| /all | 次のブート後に、インストールされているすべてのドライバーを検証するようにドライバー検証ユーティリティに指示します。 |
| /bootmode `[persistent | disableafterfail | oneboot | resetonunusualshutdown]` | 再起動後にドライバー検証ユーティリティの設定を有効にするかどうかを制御します。 このオプションを設定または変更するには、コンピューターを再起動する必要があります。 次のモードを使用できます。<ul><li>[**永続**化]-多くの再起動に対して、ドライバーの検証ツールの設定が保持されていることを確認します (有効なまま)。 これが既定の設定です。</li><li>**disableafterfail** -Windows が起動に失敗した場合、この設定により、以降の再起動のためにドライバー検証ユーティリティが無効になります。</li><li>**oneboot** -次回コンピューターを起動するときに、ドライバーの検証ツールの設定を有効にします。 その後の再起動では、ドライバー検証ユーティリティは無効になっています。</li><li>**resetonunusualshutdown** -ドライバー検証ユーティリティは、異常なシャットダウンが発生するまで保持されます。 Abbrevation ' rous ' を使用できます。</li></ul> |
| /driver `<driverlist>` | 検証される1つ以上のドライバーを指定します。 **Driverlist**パラメーターは、 *driver.sys*など、バイナリ名別のドライバーの一覧です。 各ドライバー名を区切るにはスペースを使用します。 などのワイルドカード値は `n*.sys` サポートされていません。 |
| /driver、除外 `<driverlist>` | 検証から除外する1つ以上のドライバーを指定します。 このパラメーターは、すべてのドライバーが検証対象として選択されている場合にのみ適用されます。 **Driverlist**パラメーターは、 *driver.sys*など、バイナリ名別のドライバーの一覧です。 各ドライバー名を区切るにはスペースを使用します。 などのワイルドカード値は `n*.sys` サポートされていません。 |
| /障害 | ドライバー検証ユーティリティの **低リソースシミュレーション** 機能を有効にします。 の代わりに、 **/障害** を使用でき `/flags 0x4` ます。 ただし、 `/flags 0x4` **/障害** サブパラメーターと共にを使用することはできません。 次のサブパラメーターを使用して、低リソースシミュレーションを構成することができます。<ul><li>**Probability** -ドライバー検証ユーティリティが特定の割り当てに失敗する確率を指定します。 1万での確率を表す数値 (10 進数または16進数) を入力します。これにより、ドライバー検証ユーティリティが割り当てに失敗します。 既定値は600で、600/10000 または6% を意味します。</li><li>**プールタグ** -ドライバー検証ユーティリティが、指定されたプールタグを使用した割り当てに失敗する可能性がある割り当てを制限します。 ワイルドカード文字 () を使用して、複数のプールタグを表すことができ*ます。複数のプールタグを一覧表示するには、タグをスペースで区切ります。既定では、すべての割り当てが失敗する可能性があります。 </li> <li>* * アプリケーション**-ドライバー検証ユーティリティが、指定されたプログラムの割り当てに失敗する可能性がある割り当てを制限します。 実行可能ファイルの名前を入力します。 プログラムを一覧表示するには、プログラム名をスペースで区切ります。 既定では、すべての割り当てが失敗する可能性があります。</li><li>**Delaymins** -ドライバー検証ユーティリティが意図的に割り当てを失敗させない、起動後の時間 (分単位) を指定します。 この遅延により、ドライバーが読み込まれ、テストが開始される前にシステムが安定化されます。 数値 (10 進数または16進数) を入力します。 既定値は 7 (分) です。</li></ul> |
| /faultssystematic | **体系的な低リソース**シミュレーションのオプションを指定します。 フラグを使用し `0x40000` て、 **体系的な低リソース** シミュレーションオプションを選択します。 次のオプションを使用できます。<ul><li>**enableboottime** -コンピューターの再起動によるエラー挿入を可能にします。</li><li>**disableboottime** -コンピューターの再起動によるフォールトインジェクションを無効にします (これは既定の設定です)。</li><li>**recordboottime** -コンピューターの再起動に伴う if モードでのフォールトインジェクションを有効にします。</li><li>**resetboottime** -コンピューターの再起動によるフォールトインジェクションを無効にし、スタック除外リストをクリアします。</li><li>**enableruntime** -フォールトインジェクションを動的に有効にします。</li><li>**disableruntime** -フォールトインジェクションを動的に無効にします。</li><li>**recordruntime** -what-if モードでのフォールトインジェクションを動的に有効にします。</li><li>**resetruntime** -エラーインジェクションを動的に無効にし、以前にエラーが発生したスタック一覧をクリアします。</li><li>**querystatistics** -現在のフォールトインジェクションの統計を表示します。</li><li>**incrementcounter** -エラーが挿入されたことを識別するために使用されるテストパスカウンターをインクリメントします。</li><li>**GETSTACKID COUNTER** -指定された挿入されたスタック識別子を取得します。</li><li>**EXCLUDESTACK STACKID** -フォールト挿入からスタックを除外します。</li></ul> |
| /flags `<options>` | 次回の再起動後に、指定したオプションをアクティブにします。 この数値は、10進数で入力することも、16進数 (0x プレフィックスを含む) 形式で入力することもできます。 次の値の任意の組み合わせを使用できます。<ul><li>**値: 1 または 0x1 (ビット 0)**  - [特別なプールチェック](https://docs.microsoft.com/windows-hardware/drivers/devtest/special-pool)</li><li>**値: 2 または 0x2 (ビット 1)**  - [強制 IRQL チェック](https://docs.microsoft.com/windows-hardware/drivers/devtest/force-irql-checking)</li><li>**値: 4 または 0x4 (ビット 2)**  - [低リソースシミュレーション](https://docs.microsoft.com/windows-hardware/drivers/devtest/low-resources-simulation)</li><li>**値: 8 または 0x8 (ビット 3)**  - [プールの追跡](https://docs.microsoft.com/windows-hardware/drivers/devtest/pool-tracking)</li><li>**値:16 または 0x10 (ビット 4)**  - [I/o の検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/i-o-verification)</li><li>**値:32 または 0x20 (ビット 5)**  - [デッドロック検出](https://docs.microsoft.com/windows-hardware/drivers/devtest/deadlock-detection)</li><li>**値:64 または 0x40 (ビット 6)**  - 強化された[I/o 検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/enhanced-i-o-verification)。 このオプションは、[ **I/o 検証**] を選択すると自動的にアクティブ化されます。</li><li>**値: 128 または 0x80 (ビット 7)**  - [DMA の検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/dma-verification)</li><li>**値: 256 または 0x100 (ビット 8)**  - [セキュリティチェック](https://docs.microsoft.com/windows-hardware/drivers/devtest/security-checks)</li><li>**値: 512 または 0x200 (ビット 9)**  - [保留中の I/o 要求を強制](https://docs.microsoft.com/windows-hardware/drivers/devtest/force-pending-i-o-requests)する</li><li>**値: 1024 または 0x400 (ビット 10)**  - [IRP ログ](https://docs.microsoft.com/windows-hardware/drivers/devtest/irp-logging)</li><li>**値: 2048 または 0x800 (ビット 11)**  - [その他のチェック](https://docs.microsoft.com/windows-hardware/drivers/devtest/miscellaneous-checks)</li><li>**値: 8192 または 0x2000 (ビット 13)**  - [スタックの不変の MDL チェック](https://docs.microsoft.com/windows-hardware/drivers/devtest/invariant-mdl-checking-for-stack)</li><li>**値: 16384 または 0x4000 (ビット 14)**  - [ドライバーの不変の MDL チェック](https://docs.microsoft.com/windows-hardware/drivers/devtest/invariant-mdl-checking-for-driver)</li><li>**値: 32768 または 0x8000 (ビット 15)**  - [Power Framework 遅延ファジー](https://docs.microsoft.com/windows-hardware/drivers/devtest/concurrency-stress-test)</li><li>**値: 65536 またはの値 (ビット 16)** -ポート/ミニポートのインターフェイスチェック</li><li>**値: 131072 または 0x20000 (ビット 17)**  - [DDI のコンプライアンスチェック](https://docs.microsoft.com/windows-hardware/drivers/devtest/ddi-compliance-checking)</li><li>**値: 262144 または 0x40000 (bit 18)**  - [体系的な低リソースシミュレーション](https://docs.microsoft.com/windows-hardware/drivers/devtest/systematic-low-resource-simulation)</li><li>**値: 524288 または 0x80000 (ビット 19)**  - [DDI 準拠の確認 (追加)](https://docs.microsoft.com/windows-hardware/drivers/devtest/ddi-compliance-checking)</li><li>**値: 2097152 または 0x200000 (ビット 21)**  - [NDIS/WIFI の検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/ndis-wifi-verification)</li><li>**値: 8388608 または 0x800000 (ビット 23)**  - [カーネル同期遅延ファジー](https://docs.microsoft.com/windows-hardware/drivers/devtest/kernel-synchronization-delay-fuzzing)</li><li>**値: 16777216 または 0x1000000 (ビット 24)**  - [VM スイッチの検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/vm-switch-verification)</li><li>**値: 33554432 または 0x2000000 (ビット 25)** -コードの整合性チェック。 この方法を使用して、SCSI 検証オプションまたは Storport 検証オプションをアクティブ化することはできません。 詳細については、「 [SCSI 検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/scsi-verification) と [Storport 検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/dv-storport-verification)」を参照してください。</li></ul> |
| /flags `<volatileoptions>` | 再起動せずに直ちに変更されるドライバー検証ユーティリティオプションを指定します。この数値は、10進数で入力することも、16進数 (0x プレフィックスを含む) 形式で入力することもできます。 次の値の任意の組み合わせを使用できます。<ul><li>**値: 1 または 0x1 (ビット 0)** -特別なプール</li><li>**値: 2 または 0x2 (ビット 1)** -強制 IRQL チェック</li><li>**値: 4 または 0x4 (ビット 2)** -低リソースシミュレーション</li></ul> |
| `<probability>` | 1 ~ 10,000 フォールト インジェクション確率を指定する値。 たとえば、100 を指定するには、1% (100/10,000) のフォールト インジェクション確率を意味します。<p>このパラメーターが指定されていない場合、既定の確率である6% が使用されます。 |
| `<tags>` | 空白文字で区切られた、フォールトが挿入され、プール タグを指定します。 このパラメーターが指定されていない場合、エラー、プールの割り当てを挿入できます。 |
| `<apps>` | エラーが挿入されるアプリのイメージファイル名を空白文字で区切って指定します。 このパラメーターが指定されていない場合は、すべてのアプリケーションで低リソースのシミュレーションを実行できます。 |
| `<minutes>` | 正の数値を分単位での再起動後に期間の長さを指定する正の挿入が発生します。 このパラメーターが指定されていない場合は、既定の長さである *8 分* が使用されます。 |
| /iolevel `<level>` | I/o 検証のレベルを指定します。 [Level] の値を **1** に設定すると、レベル1の i/o 検証 (既定値) または **2** -レベル 1 i/o 検証とレベル 2 i/o 検証が有効になります。 I/o 検証が有効になっていない場合 (を使用 `/flags 0x10` )、 **/iolevel** は無視されます。 |
| /log `<logfilename> [/intervalseconds]` | 指定された名前を使用してログファイルを作成します。 ドライバー検証ユーティリティは、必要に応じて設定した間隔に基づいて、このファイルに統計を定期的に書き込みます。 既定の間隔は *30 秒*です。<p> コマンドラインに検証ツール **/log** コマンドが入力されている場合、コマンドプロンプトは返されません。 ログファイルを閉じてプロンプトを返すには、 **CTRL + C** キーを使用します。 再起動後にログを作成するには、もう一度ベリファイア **/log** コマンドを送信する必要があります。 |
| /rules `<option>` | 次を含む、無効にできるルールのオプション。<ul><li>**クエリ** -制御可能なルールの現在の状態が表示されます。</li><li>**リセット** -すべての規則を既定の状態にリセットします。</li><li>**既定の id** -ルール ID を既定の状態に設定します。 サポートされているルールの場合、ルール ID は、バグチェック 0xC4 (DRIVER_VERIFIER_DETECTED_VIOLATION) パラメーター1の値です。</li><li>**無効 ID** -指定した規則 ID を無効にします。 サポートされているルールの場合、ルール ID は、バグチェック 0xC4 (DRIVER_VERIFIER_DETECTED_VIOLATION) パラメーター1の値です。</li></ul> |
| /standard | 次回の再起動後に、"standard" または既定のドライバー検証ツールオプションをアクティブにします。 標準オプションは、特別なプール、強制 IRQL チェック、プール追跡、i/o 検証、デッドロック検出、DMA 検証、セキュリティチェック、その他のチェック、および DDI 準拠チェックです。 これは、`/flags 0x209BB` と同じです。<p>[!NOTE] 1803より後のバージョンの Windows 10 以降では、を使用して `/flags 0x209BB` WDF の検証を自動的に有効にすることはできなくなりました。 標準のオプションを有効にするには **、標準の構文を** 使用します。 WDF の検証が含まれています。 |
| /volatile | コンピューターを再起動せずに設定を変更します。 揮発性の設定は直ちに有効になります。<p>**/Volatile**パラメーターと **/flags**パラメーターを使用して、再起動せずに一部のオプションを有効または無効にすることができます。 また、ドライバー検証ユーティリティが実行されていない場合でも、 **/adddriver**パラメーターと **/removedriver**パラメーターを指定して **/volatile**を使用して、再起動せずにドライバーの検証を開始または停止することもできます。 詳細については、「 [Volatile 設定の使用](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-volatile-settings)」を参照してください。 |
| /adddriver `<volatiledriverlist>` | 指定されたドライバーを揮発性の設定から削除します。 複数のドライバーを指定するには、名前をスペースで区切って指定します。 *n.sys*などのワイルドカード値はサポートされていません。 |
| /removedriver `<volatiledriverlist>` |
| /reset | すべてのドライバー検証ユーティリティの設定をクリアします。 次回の再起動後、ドライバーは検証されません。 |
| /querysettings | アクティブ化されるオプションの概要と、次回の起動時に検証されるドライバーが表示されます。 このディスプレイには、 **/volatile** パラメーターを使用して追加されたドライバーとオプションは含まれていません。 これらの設定を表示する他の方法については、「 [ドライバーの検証の設定](https://docs.microsoft.com/windows-hardware/drivers/devtest/viewing-driver-verifier-settings)を表示する」を参照してください。 |
| /query | Driver Verifier ユーティリティの現在のアクティビティの概要が表示されます。 表示の **Level** フィールドは、 **/volatile** パラメーターで設定されたオプションの16進数の値です。 各統計の説明については、「 [グローバルカウンターの監視](https://docs.microsoft.com/windows-hardware/drivers/devtest/monitoring-global-counters) と [個々のカウンターの監視](https://docs.microsoft.com/windows-hardware/drivers/devtest/monitoring-individual-counters)」を参照してください。 |
| /domain `<types> <options>` | 検証ツールの拡張機能の設定を制御します。 次の種類の検証拡張機能がサポートされています。<ul><li>**wdm** -wdm ドライバーの検証拡張機能を有効にします。</li><li>**ndis** -ネットワークドライバーの検証拡張機能を有効にします。</li><li>**ks** -カーネルモードストリーミングドライバーの検証拡張機能を有効にします。</li><li>**audio** -オーディオドライバーの検証拡張機能を有効にします。</li></ul>. 次の拡張オプションがサポートされています。<ul><li>**rules. default** -選択された検証拡張機能の既定の検証規則を有効にします。</li><li>**rules. all** -選択した検証機能拡張のすべての検証規則を有効にします。</li></ul> |
| /ログ | 選択した検証機能拡張によって検出された、違反したルールのログ記録を有効にします。 |
| /livedump | 選択した検証機能拡張によって検出された規則に違反した場合に、ライブメモリダンプの収集を有効にします。 |
| /? | コマンドラインのヘルプを表示します。 |

### <a name="return-codes"></a>リターン コード

ドライバーの検証ツールを実行すると、次の値が返されます。

- 0: EXIT_CODE_SUCCESS

- 1: EXIT_CODE_ERROR

- 2: EXIT_CODE_REBOOT_NEEDED

#### <a name="remarks"></a>解説

- **/Volatile**パラメーターは、Driver Verifier ユーティリティの **/flags**オプションと、 **/標準**の一部で使用できます。 **/Flags**オプションと共に **/volatile**を使用して、 [DDI 準拠の確認](https://docs.microsoft.com/windows-hardware/drivers/devtest/ddi-compliance-checking)、[電源フレームワーク遅延ファジー](https://docs.microsoft.com/windows-hardware/drivers/devtest/concurrency-stress-test)化、 [Storport 検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/dv-storport-verification)、または[SCSI 検証](https://docs.microsoft.com/windows-hardware/drivers/devtest/scsi-verification)を行うことはできません。 詳細については、「 [Volatile 設定の使用](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-volatile-settings)」を参照してください。

## <a name="additional-references"></a>その他のリファレンス

- [コマンド ライン構文の記号](command-line-syntax-key.md)

- [ドライバーの検証ツール](https://docs.microsoft.com/windows-hardware/drivers/devtest/driver-verifier)

- [ドライバーの検証ツールの制御](https://docs.microsoft.com/windows-hardware/drivers/devtest/controlling-driver-verifier)

- [ドライバーの検証ツールの監視](https://docs.microsoft.com/windows-hardware/drivers/devtest/monitoring-driver-verifier)

- [揮発性の設定の使用](https://docs.microsoft.com/windows-hardware/drivers/devtest/using-volatile-settings)
