---
title: サーバー バックアップのセットアップまたはカスタマイズ
description: Windows Server Essentials を使用する方法について説明します
ms.custom: na
ms.date: 10/03/2016
ms.prod: windows-server-2016-essentials
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 441c2d6c-435a-42cb-90f2-6d680d279d34
author: nnamuhcs
ms.author: coreyp
manager: dongill
ms.openlocfilehash: 727dd74e4bddc52f735969f216914b9d76d1f413
ms.sourcegitcommit: 0d0b32c8986ba7db9536e0b8648d4ddf9b03e452
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/17/2019
ms.locfileid: "59831933"
---
# <a name="set-up-or-customize-server-backup"></a>サーバー バックアップのセットアップまたはカスタマイズ

>適用先:Windows Server 2016 Essentials、Windows Server 2012 R2 Essentials、Windows Server 2012 Essentials
  
 サーバーのバックアップがインストール時に自動的に構成されることはありません。 日次バックアップのスケジュールを設定して、サーバーとサーバー上のデータを自動的に保護する必要があります。 ほとんどの組織は数日間作成されたデータを失う余裕はないため、毎日のバックアップ計画を維持することをお勧めします。  
  
 サーバーのバックアップをセットアップまたはカスタマイズするには、以下のセクションを参照してください。  
  
-   [設定またはサーバーのバックアップ設定を変更します。](Set-up-or-customize-server-backup.md#BKMK_1)  
  
-   [サーバー バックアップのスケジュール](Set-up-or-customize-server-backup.md#BKMK_2)  
  
-   [バックアップ先のドライブ](Set-up-or-customize-server-backup.md#BKMK_Target)  
  
-   [バックアップする項目](Set-up-or-customize-server-backup.md#BKMK_4)  
  
##  <a name="BKMK_1"></a> 設定またはサーバーのバックアップ設定を変更します。  
  
#### <a name="to-set-up-or-change-server-backup-settings"></a>サーバー バックアップの設定をセットアップまたは変更するには  
  
1.  **ダッシュボード**を開き、**[デバイス]** タブをクリックします。  
  
2.  リスト ビューで、目的のサーバーをクリックして選択します。  
  
3.  作業ウィンドウで、 **[サーバーのバックアップのセットアップ]** をクリックします。  
  
    > [!NOTE]
    >  既存のバックアップの設定を変更する場合は、 **[サーバーのバックアップのカスタマイズ]** をクリックします。  
  
4.  ウィザードの指示に従います。  
  
    > [!NOTE]
    >  サーバーに外付けハード ドライブを接続する前にウィザードを開始した場合は、ハード ドライブを接続した後、 **[バックアップ先の選択** ] ページの **[一覧を最新の情報に更新]** をクリックします。  
  
> [!NOTE]
>  Windows Server Essentials の既定のインストール、自動的に毎週 1 回最適化を実行するサーバーを構成します。 この結果、Microsoft 以外のイメージング ソフトウェアを使用すると、バックアップが通常よりも大きくなります。 サーバーを定期的に最適化する必要がない場合は、次の手順に従って最適化スケジュールを無効にすることができます。  
>   
>  1.  Windows キー + W キーを押して、**[検索]** を開きます。  
> 2.  [検索] ボックスに「**Defragment**」と入力します。  
> 3.  表示された検索結果のセクションで、 **[ドライブのデフラグと最適化]** をクリックします。  
> 4.  **[ドライブの最適化]** ウィンドウでドライブを選択し、**[設定の変更]** をクリックします。  
> 5.  **[最適化のスケジュール]** ウィンドウで **[スケジュールに従って実行する (推奨)]** チェック ボックスをオフにし、**[OK]** をクリックして変更を保存します。  
  
##  <a name="BKMK_2"></a> サーバー バックアップのスケジュール  
 サーバー バックアップのセットアップ ウィザードまたはサーバー バックアップのカスタマイズ ウィザードを使用する場合、サーバー データを 1 日に複数回バックアップするように選択できます。 これらのウィザードでは、増分ベースのバックアップのスケジュールが設定されるため、バックアップは高速に実行され、サーバーのパフォーマンスに大幅な影響はありません。 既定では、ウィザードはバックアップを毎日午後 12:00 と午後 11:00 に実行するようにスケジュールを設定します。 ただし組織のニーズに合わせて、バックアップ スケジュールを調整できます。 場合によっては、バックアップ計画の有効性を評価し、必要に応じて計画を変更します。  
  
##  <a name="BKMK_Target"></a> バックアップ先のドライブ  
 複数の外部記憶域ドライブをバックアップに使用し、オンサイトとオフサイトの記憶域場所をローテーションすることができます。 これにより、オンサイトのハードウェアで物理的破損が発生しても、データの回復がサポートされるため、障害対策計画を向上させることができます。  
  
 サーバー バックアップ用にストレージ ドライブを選択した場合、以下の点を考慮してください。  
  
-   データを保存するための十分な空き領域が含まれているドライブを選択します。 記憶域ドライブには、バックアップ対象のデータよりも少なくとも 2.5 倍の記憶域容量があるドライブを使用してください。 またドライブは、将来の増加に対応できるだけの十分な容量を備えている必要があります。  
  
-   外部記憶域ドライブを使用する場合は、ドライブが空であること、または不要なデータしか含まれていないことを確認してください。  
  
    > [!CAUTION]
    >  サーバー バックアップのセットアップ ウィザードがバックアップ用に記憶域ドライブを構成すると、それらのドライブはフォーマットされます。  
  
-   バックアップ対象となるドライブにオフライン ドライブが含まれる場合、バックアップ構成は正常に終了しません。 構成を完了するには、バックアップ対象を選択する場合に、オフラインのドライブを除外するチェック ボックスをオフにします。  
  
-   ウィザードの使用時に、バックアップ対象として以前のバックアップが含まれているドライブを選択すると、以前のバックアップを保持するか選択することができます。 バックアップを保持する場合、ウィザードは、ドライブをフォーマットしません。  
  
-   Windows Server Essentials を実行するコンピューターで、バックアップ ドライブがサポートされていることを確認する、外部ストレージ ドライブの製造元の web サイトにアクセスする必要があります。  
  
-   ドライブに拡張ファームウェア インターフェイス (EFI) システム パーティションが含まれていてはなりません。 USB ドライブに EFI パーティションが存在する場合、ディスクは起動ディスクと見なされます。 必要、ディスク上のデータを使用しない場合は、ディスクを再フォーマットし、バックアップに使用できます。  
  
    > [!CAUTION]
    >  ディスクを再フォーマットすると、すべてのデータが削除されます。  
  
    #### <a name="to-remove-an-efi-system-partition-from-a-usb-disk"></a>USB ディスクから EFI システム パーティションを削除するには  
  
    1.  コントロール パネルの **[システムとセキュリティ]** を開きます。  
  
    2.  **[管理ツール]** の **[ハード ディスク パーティションの作成とフォーマット]** をクリックします。  
  
    3.  USB ディスクにあるすべてのボリュームを削除するか、EFI パーティションのみを削除します。 サーバー バックアップのセットアップ ウィザードにより、すべてのボリュームが削除されます。  
  
-   ドライブに共有サーバー フォルダーが含まれていてはなりません。 ディスクをバックアップの対象ドライブとして使用するには、共有サーバー フォルダーの共有を停止する必要があります。 共有の停止は、ダッシュボードまたはエクスプローラーから行うことができます。  
  
    #### <a name="to-stop-sharing-on-a-server-folder-from-the-dashboard"></a>ダッシュボードからサーバー フォルダーの共有を停止するには  
  
    1.  ダッシュボードの **[記憶域]** をクリックし、**[サーバー フォルダー]** をクリックします。  
  
    2.  共有を停止するフォルダーを選択し、タスク ウィンドウで **[停止]** をクリックします。  
  
> [!NOTE]
>  バックアップ ドライブに十分な空き領域が必要があるため、バックアップが成功しなかった場合、バックアップ対象ドライブのドライブ文字は、Windows Server Essentials データベースから削除し、ダッシュ ボードでは、ドライブは表示されません。 そのドライブを今後のバックアップで使用する場合は、ネイティブ ツールを使用してドライブ文字を再割り当てする必要があります。  
>   
>  **既存のボリュームのドライブ文字を再割り当てするには**  
>   
>  1.  コントロール パネルの **[システムとセキュリティ]** を開きます。  
> 2.  **[管理ツール]** の **[ハード ディスク パーティションの作成とフォーマット]** をクリックします。  
> 3.  ドライブを右クリックし、**[ドライブ文字とパスの変更]** をクリックします。  
> 4.  **[追加]** をクリックします。  
> 5.  [ドライブ文字またはパスの追加] ダイアログ ボックスで、割り当てるドライブ文字を選択します。 (同じドライブ文字を再割り当てすることができます。)**[OK]** をクリックします。  
>   
>      ドライブは直ちにダッシュボードに表示されます。  
  
##  <a name="BKMK_4"></a> バックアップする項目  
 サーバー上のすべてのドライブ、ファイル、およびフォルダーをバックアップするように選択することも、個別のドライブ、ファイル、またはフォルダーだけをバックアップするように選択することもできます。  
  
 ドライブを追加または削除した場合、あるいは共有ファイルやフォルダーを追加または削除した場合は、サーバー バックアップ構成を再確認し、これらの項目がバックアップ構成に対して追加または削除されたことを確認してください。 バックアップする項目を追加または削除するには、以下のいずれかを行います。  
  
-   サーバー バックアップにデータ ドライブを挿入するには、隣接するチェック ボックスをオンにします。  
  
-   サーバー バックアップからデータ ドライブを除外するには、隣接するチェック ボックスをオンにします。  
  
    > [!NOTE]
    >  バックアップから **[オペレーティング システム]** 項目を除外するには、最初に **[システム バックアップ (推奨)]** チェック ボックスをオフにします。  
  
 サーバー バックアップに使用するサーバー記憶域の容量を最小限にするため、特段の重要性がないと判断したファイルを含むフォルダーは除外することをお勧めします。  
  
 たとえば大量のハード ドライブ容量を使用する、テレビ番組の録画が記録されているフォルダーがあるとします。 通常、これらのファイルは見終わった後に削除するため、これらのファイルをバックアップしないことを選択できます。 または、保持することを目的としない一時ファイルが含まれているフォルダーが存在している場合もあります。  
  
## <a name="see-also"></a>関連項目  
  
-   [サーバー バックアップを管理します。](Manage-Server-Backup-in-Windows-Server-Essentials.md)  
  
-   [バックアップの管理と復元](Manage-Backup-and-Restore-in-Windows-Server-Essentials.md)  
  
-   [Windows Server Essentials を管理します。](Manage-Windows-Server-Essentials.md)  
  
-   [Windows Server Essentials を使用します。](../use/Use-Windows-Server-Essentials.md)